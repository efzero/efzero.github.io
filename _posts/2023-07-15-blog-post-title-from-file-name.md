

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
