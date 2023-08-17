

### Diffusion

Even though we introduce a few hyperparameters, we found that our method can be easily adapted to new tasks (inverse problems), and the hyperparameters are straightforward to tune. Actually, we use the same set of hyperparameters for all natural images experiments and only change a little for medical images experiments. We provide the reason in the table below:
|  Hyperparameter Name  | Purpose  |  Tuning difficulty |
| :----- | :---------: | ---------: |
|$\lambda$ and $\tau$ | measurement consistency optimization | only depend on noise level and only require one ground truth image to tune. We use the same values of $\lambda$ and $\tau$ for natural image experiments and the same values for medical image experiments|
|$C = \{1,...T \}$  | Time steps for data consistency | does not require tuning (only for accelerating the inferencing process). we use the same value for every problem |
| $\eta$ | control the tradeoff between prior consistency and measurement consistency | We tune it based on one ground truth CT image, and use the same value of it for every task (both medical images and natural images), Figure 9 demonstrates that there is no large performance change when there is a small change in $\eta$|
| $k$ | Time travel steps for $\hat{z}_0$ | only requires one ground truth image to tune, and performance changes little as $k$ changes as shown in Table 8. We use the same $k$ for every task. Empirically, we use $k = 2c$ where $c$ is the size of skip step for data consistency |


### Why Hard Consistency (why not add hard consistency on top of Latent-DPS):
1. Since the latent diffusion model is highly nonlinear and nonconvex, the gradient update from Latent-DPS may not improve the measurement consistency and may cause the reconstructed image to be very different from the ground truth image. We introduce hard consistency optimization to fix the data consistency issue.
Adding Latent-DPS gradient term to ReSample may cause the deterioration of measurement consistency since the hard data consistency update is not performed on every time step (only a small subset of all time steps), but Latent-DPS is performing gradient update on each time step. It is very likely that the Latent-DPS gradient update term worsens the measurement consistency, which ReSample tries to improve. To demonstrate this benefit, we list the average measurement consistency loss for CT reconstruction with Latent-DPS in the table below            

|     Anatomical site | ReSample (Ours) |  Latent-DPS |
| :---------------- | :------: | ----: |
| Chest      |   5.36e-5  | 2.99e-3 |
| Abdominal         |   6.28e-5   | 3.92e-3 |
| Head   |  1.73e-5   | 2.03e-3 |

2. Similar to a plug-and-play approach, the hard consistency update can iteratively refine the final reconstruction quality by injecting the measurement-consistent updates into the reverse sampling process. Ideally, this iterative hard consistency update can modify the reverse sampling trajectory of reconstruction to be closer to that of the ground truth image. Without sufficient steps of hard consistency updates, the pre-trained diffusion model is not likely to sample a good-quality image since the reverse sampling trajectory can be far from that of the ground truth image.  We demonstrated this phenomenon in Appendix Table 7: the more hard consistency update steps, the better reconstruction quality we got. 


### Comparison of other baselines
We are aware of other baselines and discuss them in the table below:

|     Citation number in the paper | Name |  Reason of exclusion |
| :--| :----------: | -----------------: |
| [6]   |   Fast diffusion sampler for inverse problems by geometric decomposition  | The paper does not perform experiments on natural images, and the code is not publicly available|
| [16]    |   Denoising diffusion restoration model| In the DPS paper, it shows similar performance between DDRM and DPS. Since we use the same experimental setting in DPS (same noise level, inverse problem and dataset), we believe this result should be transferrable |
| [25]  |  Diffusion model-based posterior sampling for noisy linear inverse problems   | In the paper, it shows similar performance between itself and DPS and use the same experimental setting as DPS, we believe this result should be transferrable. Also, this algorithm requires SVD or PsuedoInverse, which is very difficult or not possible to compute for nonlinear deblurring, CT reconstruction, and motion deblurring|
| [32]  |   Pseudoinverse-guided diffusion models for inverse problems   | This algorithm requires SVD or PsuedoInverse, which is very difficult or not possible to compute for nonlinear deblurring, CT reconstruction, and motion deblurring |
| [34]  |  Solving inverse problems in medical imaging with score-based generative models  | This paper does not perform experiments on natural images, and the MCG paper shows similar or inferior performance of it comparing to MCG in a similar experimental settings as ours for CT reconstruction |
| [43]  |  Self-supervised image denoising for real-world images with context-aware transformer  | This paper is irrelevant to our tasks here |




### A new proposition to show that ReSample is more likely to escape from the hypothetical bad event when t decreases
For Weakness #5, we found that $Var(\hat{z}_0(t)$ is in fact decreasing as time decreases (actually decreases exponentially), and converges to 0 when time goes to 0. As a result, it becomes less likely that we encounter bad events as t decreases. We present a new proposition below to show this. 

**Proposition 1**. $Var(z_0 | z_t) = \frac{(1 - \alpha_t)^2}{\alpha_t}\nabla^2_{z_t}\log p_{z_t}(z_t) + \frac{1 - \alpha_t}{\alpha_t} $

Proof: we use the Tweedie's formula for the exponential family and apply the change of variable of $z_t$. We construct a variable $\bar{z}_t = \frac{\sqrt{\alpha_t}}{ 1 - \alpha_t}z_t$, now we have $$p(\bar{z}_t | z_0) = \frac{1}{(2\pi (\frac{\alpha_t}{1-\alpha_t}))^{d/2}}\exp(-\frac{||\bar{z}_t - \frac{\alpha_t}{1-\alpha_t}z_0||^2}{2(\frac{\alpha_t}{1 - \alpha_t})})$$, we want to separate the term only with $\bar{z}_t$ and the term only with $z_0$ for applying Tweedie's formula. Hence let $p_0(\bar{z}_t) = \frac{1}{(2\pi (\frac{\alpha_t}{1-\alpha_t}))^{d/2}}\exp(-\frac{||\bar{z}_t ||^2}{2(\frac{\alpha_t}{1 - \alpha_t})})$, we achieve $p(\bar{z}_t | z_0) = p_0(\bar{z}_t) \exp({\bar{z}_t}^Tz_0 - \frac{\alpha_t}{2(1-\alpha_t)} ||z_0||^2)$ 

Let $\lambda(\bar{z}_t) = \log p(\bar{z}_t) - \log p_0(\bar{z}_t)$ By Tweedie's formula if this distribution holds, then we will have $\mathbb{E}[z_0 | \bar{z}_t] = \nabla \lambda(\bar{z}_t)$ and $Var(z_0 | \bar{z}_t) = \nabla^2 \lambda(\bar{z}_t)$

Now we first compute expectation, since $p_0(\bar{z}_t)$  is a Gaussian with mean at 0 and variance $\frac{\alpha_t}{1-\alpha_t}$
We got  $$\nabla \lambda(\bar{z}_t) =   \nabla \log p(\bar{z}_t)  + \frac{1-\alpha_t}{\alpha_t} \bar{z}_t$$, then use chain rule and the scale of distribution formula: $p(\bar{z}_t) = \frac{1}{a}p(\frac{z_t}{a})$, we arrive at $\mathbb{E}[z_0 | z_t] = \frac{1 - \alpha_t}{\sqrt{\alpha_t}} \nabla \log p(z_t) + \frac{1}{\sqrt{\alpha_t}}z_t$, which exactly matches the formula in the DPS paper. Then we compute the derivative again and similarly we get the result.


## 3D Latent Diffusion

#### NeRF type methods

1. 3D Neural Field Generation using Triplane Diffusion (code available): [Triplane Diffusion](https://arxiv.org/pdf/2211.16677.pdf)
2. Single-Stage Diffusion NeRF: A Unified Approach to 3D Generation and Reconstruction (code available): [Diffusion-NeRF](https://lakonik.github.io/ssdnerf/)
3. One-2-3-45: Any Single Image to 3D Mesh in 45 Seconds without Per-Shape Optimization (code pending): [Single Image](https://github.com/One-2-3-45/One-2-3-45#one-2-3-45-any-single-image-to-3d-mesh-in-45-seconds-without-per-shape-optimization)


#### Video Diffusion

1. Latent Video Diffusion Models for High-Fidelity Long Video Generation [Video Diffusion](https://arxiv.org/pdf/2211.13221.pdf)
2. MagicVideo: Efficient Video Generation With Latent Diffusion Models [Video Diffusion 2](https://arxiv.org/pdf/2211.11018.pdf)
3. Align your Latents: High-Resolution Video Synthesis with Latent Diffusion Models [Latent Video Diffusion](https://research.nvidia.com/labs/toronto-ai/VideoLDM/)



#### Architecture of Diffusion NeRF

<p align="center">
 <img src="https://github.com/efzero/PINER/blob/master/networks/Screen%20Shot%202023-07-20%20at%206.26.14%20PM.png?raw=true" width="1000" height="400">
</p>

<p align="center">
  <img src="https://github.com/efzero/PINER/blob/master/networks/Screen%20Shot%202023-07-20%20at%206.18.26%20PM.png?raw=true" width="500" height="400">
</p>



##### Results for Sparse-View Reconstruction

<p align="center">
 <img src="https://github.com/efzero/PINER/blob/master/networks/Screen%20Shot%202023-07-20%20at%206.48.24%20PM.png?raw=true" widht="1000" height="400">

 </p>


---

### This is a header

#### Some T-SQL Code

```tsql
SELECT This, [Is], A, Code, Block -- Using SSMS style syntax highlighting
    , REVERSE('abc')
FROM dbo.SomeTable s
    CROSS JOIN dbo.OtherTable o;
```

#### Some PowerShell Code

```powershell
Write-Host "This is a powershell Code block";

# There are many other languages you can use, but the style has to be loaded first

ForEach ($thing in $things) {
    Write-Output "It highlights it using the GitHub style"
}
```
