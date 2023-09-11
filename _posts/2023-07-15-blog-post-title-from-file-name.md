

## 3D Latent Diffusion

#### NeRF type methods

1. 3D Neural Field Generation using Triplane Diffusion (code available): [Triplane Diffusion](https://arxiv.org/pdf/2211.16677.pdf)
2. Single-Stage Diffusion NeRF: A Unified Approach to 3D Generation and Reconstruction (code available): [Diffusion-NeRF](https://lakonik.github.io/ssdnerf/)
3. One-2-3-45: Any Single Image to 3D Mesh in 45 Seconds without Per-Shape Optimization (code pending): [Single Image](https://github.com/One-2-3-45/One-2-3-45#one-2-3-45-any-single-image-to-3d-mesh-in-45-seconds-without-per-shape-optimization)


#### Video Diffusion

1. Latent Video Diffusion Models for High-Fidelity Long Video Generation [Video Diffusion](https://arxiv.org/pdf/2211.13221.pdf)
2. MagicVideo: Efficient Video Generation With Latent Diffusion Models [Video Diffusion 2](https://arxiv.org/pdf/2211.11018.pdf)
3. Align your Latents: High-Resolution Video Synthesis with Latent Diffusion Models [Latent Video Diffusion](https://research.nvidia.com/labs/toronto-ai/VideoLDM/) [Latent CVPR](https://openaccess.thecvf.com/content/CVPR2023/papers/Blattmann_Align_Your_Latents_High-Resolution_Video_Synthesis_With_Latent_Diffusion_Models_CVPR_2023_paper.pdf) (combining a SR DM and LDM) **This is can used together with a 2D image latent diffusion model (e.g. stable diffusion)**, The key idea is **Adjust the latent vector by a 3D temporal network**
 Training
   1. first use latent 2D diffusion encoder to obtain a code (spatial step) for 
   2. then use temporal network to adjust the latent code, and combine with the original code (a convex combination)
   3. Do this for a couple of times
Inference.
5. Video Probabilistic Diffusion Models in Projected Latent Space
   1. Use the triplane idea (xy, xz, yz) latent codes (using 2D diffusion instead of 3D diffusion)
   2. First use video transformer to compress video C X H X W -> C X H' X W'
   3. Then use three small transformers to project 3D into 2D i.e. $z_h = f_{\theta}(u_h)$, $z_w = f_{\theta}(u_w)$, $z_c = f_{\theta}(u_c)$ reducing space complexity to $O(HWC)$ to $O(HW) + O(CW) + O(HC)$
  
#### Long Video Generation
1. NUWA-XL: Diffusion over Diffusion
for eXtremely Long Video Generation (Coarse to Fine model). Coarse diffusion with a fine diffusion: https://arxiv.org/pdf/2303.12346.pdf
2. VideoFusion: Decomposed Diffusion Models for High-Quality Video Generation, https://arxiv.org/pdf/2303.08320.pdf, generate residual due to highly correlated frames

3. Flexible Diffusion Modeling of Long Videos: https://arxiv.org/pdf/2205.11495.pdf, conditional generation
4. Video Diffusion Models https://arxiv.org/abs/2212.00235, 3D UNet
5. VIDM: Video Implicit Diffusion Models https://arxiv.org/pdf/2212.00235.pdf combining a motion generator and a content generator. with normalization (INR like)
6. Video Diffusion Models with Local-Global Context Guidance https://arxiv.org/pdf/2306.02562.pdf Global context and local context
7. Animate-A-Story:
Storytelling with Retrieval-Augmented Video Generation https://arxiv.org/pdf/2307.06940.pdf

#### Visual AutoPrompting
1. ReGeneration Learning of Diffusion Models with Rich Prompts for Zero-Shot
Image Translation https://arxiv.org/pdf/2305.04651.pdf, use GPT3 to change prompt and edit image
2. Negative-prompt Inversion: Fast Image Inversion for
Editing with Text-guided Diffusion Models image editting without optimization. https://arxiv.org/pdf/2305.16807.pdf
3. Visual Instruction Inversion:
Image Editing via Visual Prompting https://arxiv.org/pdf/2307.14331.pdf
4. Generative Visual Prompt: Unifying Distributional Control of Pre-Trained Generative Models https://arxiv.org/abs/2209.06970
##### Test-time Adaptation
5. Prompting Diffusion Representations for
Cross-Domain Semantic Segmentation: https://arxiv.org/pdf/2307.02138.pdf use prompt to improve generalization ability of diffusion models


#### Inverse Problem
1. Diffusion with Forward Models: Solving Stochastic
Inverse Problems Without Direct Supervision https://arxiv.org/pdf/2306.11719.pdf
#### Other Related Works
1. MAGVIT: Masked Generative Video Transformer: https://arxiv.org/pdf/2212.05199.pdf
2. MCVD: Masked Conditional Video Diffusion for
Prediction, Generation, and Interpolation https://arxiv.org/pdf/2205.09853.pdf masked methods like MAE etc
3. Diffusion Models as Masked Autoencoders https://arxiv.org/abs/2304.03283
4. DIFFUSION MODELS ALREADY HAVE A SEMANTIC LATENT SPACE https://arxiv.org/pdf/2210.10960.pdf
5. ChatCAD: Interactive Computer-Aided Diagnosis on Medical Image using Large Language Models https://arxiv.org/pdf/2302.07257.pdf
6. Visual Instruction Tuning: https://arxiv.org/pdf/2304.08485.pdf
7. Adversarial Discriminative Domain Adaptation https://arxiv.org/pdf/1702.05464.pdf
8. Steerable Conditional Diffusion for Out-of-Distribution Adaptation in Imaging Inverse Problems https://arxiv.org/pdf/2308.14409.pdf



sketch to image. VAE -> shared feature with downgraded image. (maybe try latent diffusion embedding)
lora, text, change model itself, controlnet
### VPDM Architecture ###

<p align="center">
 <img src="https://github.com/efzero/PINER/blob/master/networks/Screen%20Shot%202023-08-31%20at%209.11.40%20PM.png?raw=true" width="1000" height="400">
</p>

### Triplane Representation of Knee MRI image ###

<p align="center">
 <img src="https://github.com/efzero/PINER/blob/master/networks/triplane_agg.png?raw=true" width="400" height="400">
</p>

<p align="center">
 <img src="https://github.com/efzero/PINER/blob/master/networks/triplane_dim0.png?raw=true" width="400" height="400">
</p>

<p align="center">
 <img src="https://github.com/efzero/PINER/blob/master/networks/triplane_dim2.png?raw=true" width="400" height="400">
</p>


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
