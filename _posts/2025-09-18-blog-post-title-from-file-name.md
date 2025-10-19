# Controllable and Constrained Sampling (CCS): Revealing Linearity in Diffusion Sampling

### ✨ Introduction

Diffusion models have become the foundation of modern generative modeling, powering text-to-image systems like Stable Diffusion and DALL·E. Yet, the *mechanism* by which these models generate diverse yet realistic samples remains somewhat mysterious.

In our recent work, **Controllable and Constrained Sampling (CCS)**, we uncover a surprisingly simple but powerful property underlying diffusion sampling—**a widely existing linearity between the input and output during DDIM sampling**.

---

## 🔍 The Hidden Linearity in DDIM Sampling

DDIM (Denoising Diffusion Implicit Models) sampling is often viewed as a nonlinear iterative denoising process. However, when we analyze the mapping between the **initial noise** \(x_T\) and the final generated sample \(x_0\), we find an almost *linear* relationship between change of outputs and change of inputs:


Empirically, this **linearity** is strikingly consistent across datasets, models, and sampling steps — indicating that DDIM sampling acts like a *linear transformation* in the high-dimensional data space.

---

## 🎛️ Controlling Samples through Linearity

This linear structure has deep implications.  
Because the output \(x_0\) depends *linearly* on the input \(x_T\), we can directly **control** the generation process by perturbing the initial noise in a principled way.

### Example: Controlling the Mean and MSE

- **Sample Mean Control:**  
  By shifting \(x_T\) in a known direction, we can predictably adjust the mean of generated samples.

- **Sample MSE Control:**  
  By scaling or projecting noise components, we can constrain the output variance or reconstruction error—without retraining the model.

In effect, CCS turns a *black-box sampler* into a *controllable generator* with explicit, mathematically interpretable levers.

---

## 🧭 Linearity as a Window into Data Distribution

Beyond controllability, linearity reveals something fundamental about the model’s understanding of the data.

When we test the same sampling process on **out-of-distribution (OOD)** data, the linear correlation between \(x_T\) and \(x_0\) sharply **deteriorates**.

This suggests that:
- High linearity corresponds to data **within the training distribution**.
- Low linearity flags **OOD or underrepresented regions**.

Thus, linearity becomes not just a control signal—but a diagnostic tool for understanding the *geometry* of the learned data manifold.

---

## 🌌 Why CCS Matters

- **Training-free:** CCS requires *no additional model training* or architectural changes.  
- **Generalizable:** Works across diverse diffusion backbones (e.g., Stable Diffusion, DiT, Video Diffusion).  
- **Interpretable:** Provides a physics-like view of how information flows through the generative process.  
- **Diagnostic:** Offers new metrics for measuring model robustness and data coverage.

---

## For details check our paper at: https://arxiv.org/abs/2502.04670

| Concept | Description |
|----------|--------------|
| **Observation** | DDIM sampling exhibits near-linear mapping from initial noise to output. |
| **Implication** | Enables direct control over sample mean, MSE, and other statistics. |
| **Insight** | Linearity reflects model’s internal understanding of the data distribution—lower for OOD data. |
| **Contribution** | CCS provides a unified, training-free framework for controllable and constrained sampling. |

---
