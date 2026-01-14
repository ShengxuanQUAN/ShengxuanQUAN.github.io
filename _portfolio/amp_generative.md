---
title: "Controllable Generative Modeling for Anti-bacterial Peptides via WAE + CLaSS"
collection: portfolio
permalink: /portfolio/amp-generative/
excerpt: "WAE + CLaSS pipeline for controllable novel AMP generation; improved robustness and multi-objective learning."
---


### Problem

**Antimicrobial resistance (AMR)** is a growing global health threat that undermines the effectiveness of existing antibiotics and increases morbidity, mortality, and healthcare burden. **Antibacterial peptides (AMPs)** offer a promising alternative: many exhibit broad-spectrum activity and can also modulate host immune responses, providing mechanisms that may reduce selective pressure and complement conventional antibiotics.

However, traditional AMP discovery and optimization are often **costly and low-throughput**, relying on limited motif families and incremental modifications of known scaffolds. This constraint makes it difficult to systematically explore the vast peptide sequence–structure space and to rapidly identify candidates with balanced properties. **AI-driven generative modeling** provides a scalable route to expand exploration, generate novel peptide conformations, and prioritize candidates under multi-objective constraints—offering a feasible computational path toward next-generation anti-infective design.

**In this project, I reproduced a controllable generative pipeline (WAE + CLaSS) to support AMP design and diagnosis, with optimization on robustness, bias analysis, and multi-objective controllability.**



### Approach
- Model: Wasserstein Autoencoder (WAE) + Controlled Latent attribute Space Sampling (CLaSS)
- Data: curated short peptide datasets; schema harmonization; labels
- Evaluation: distributional diagnostics, property-guidance .......
- Figure
<p><strong>Method flow chart</strong></p>
<img src="/images/flowchart.png" alt="Method" style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 6px;">

### Key Contributions (ongoing)
- Reproduced a WAE-based AMP generation pipeline and validated end-to-end training on a small curated dataset.
- Implemented dataset standardization and preprocessing (tokenization, splitting, export) for reproducible experiments.
- Built diagnostics for generated sequences (distributional diagnostics) and identified short-length bias in Phase 1 outputs.


### Evaluation & Reflection ( Small curated dataset test)
- Diagnostic Evaluation
- Distributional Diagnostics
<p><strong>Bias analysis of generated AMPs</strong></p>
<img src="/images/bias.png" alt="Bias analysis" style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 6px;">
<!-- Training Loss (TensorBoard) -->
<h4>Training Loss Curves (TensorBoard)</h4>

<p>
  The loss curves below were exported from TensorBoard. With a small curated dataset, 
  training for too many iterations led to late-stage instability and loss divergence 
  (i.e., the model began to overfit and the optimization became noisy), highlighting 
  the limitations of Phase 1 pretraining under data scarcity.
</p>

<div style="display: grid; grid-template-columns: 1fr; gap: 14px;">
  <figure style="margin: 0;">
    <img src="./images/Loss01.png" alt="TensorBoard: total training loss"
         style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 6px;">
    <figcaption style="font-size: 0.95em; color: #555; margin-top: 6px;">
      TensorBoard export: total training loss (late-stage divergence under small-data regime).
    </figcaption>
  </figure>

  <figure style="margin: 0;">
    <img src="./images/loss02.png" alt="TensorBoard: reconstruction loss"
         style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 6px;">
    <figcaption style="font-size: 0.95em; color: #555; margin-top: 6px;">
      TensorBoard export: reconstruction loss.
    </figcaption>
  </figure>

  <figure style="margin: 0;">
    <img src="./images/loss03.png" alt="TensorBoard: regularization loss"
         style="max-width: 100%; height: auto; border: 1px solid #ddd; border-radius: 6px;">
    <figcaption style="font-size: 0.95em; color: #555; margin-top: 6px;">
      TensorBoard export: regularization/penalty term (instability becomes more apparent late in training).
    </figcaption>
  </figure>
</div>

### Next steps
Generalization, mitigate α-helix bias, stronger multi-objective constraints.


### References
- Das, P., Sercu, T., Wadhawan, K., *et al.* (2021). **Accelerated antimicrobial discovery via deep generative models and molecular dynamics simulations.** *Nature Biomedical Engineering, 5*(6), 613–623. https://doi.org/10.1038/s41551-021-00689-x (PMID: 33707779)
