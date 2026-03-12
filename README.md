# MIGOE: Minimum Information for Generative Omics Evaluation

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)

## Overview

The MIGOE (Minimum Information for Generative Omics Evaluation) framework establishes rigorous standards for evaluating generative AI models in omics research. It addresses critical challenges in establishing trust boundaries and audit standards for clinical artificial intelligence (ACI) deployment. 

Generative omics is spearheading a paradigm leap from passive data alignment to active contextual inference. The MIGOE framework ensures that this escalation in capabilities is accompanied by rigorous auditing standards. Our goal is to shift the debate from "whether the generation is absolutely real" to "at what level of maturity a model can be held accountable for specific scientific claims," ensuring that virtual cohorts and Artificial Clinical Intelligence (ACI) serve as reliable accelerators rather than amplifiers of biases and algorithmic hallucinations.

![MIGOE Framework Overview](assets/migoe-framework-overview.png)

## Core Values

- **Trust Boundary Definition**: Clearly define the capability scope and limitations of generative omics models.
- **Audit Standards**: Provide repeatable and verifiable evaluation methodologies.
- **Clinical Translation Support**: Ensure quality assurance for ACI system deployment.
- **Community-Driven Updates**: Continuously integrate latest research and best practices.

---


## Six Core Principles

The framework strictly requires adherence to the following six core principles:

### 1. Tier Alignment & Generation Card

**Principle**: Model evaluation must align with the claimed maturity tier. Authors must disclose a transparent "Generation Card" to guard against academic misconduct such as artificially improving results.

**Key Requirements:**
- **Tier Declaration**: Specify target tier (0–4) with a concise rationale based on task complexity and data modalities.
- **Zero-shot Criteria**: Specify if target-cohort or target-modality paired data were used during pre-training, fine-tuning, or adaptation.
- **Generation Card**: Disclose output type (point estimates vs. sampled distributions), sampling frequency, random seed strategy, and post-processing/QC rules.

**Implementation Checklist:**
- [ ] Disclose output type (point estimates vs. sampled distributions).
- [ ] Document all random seeds used and generation card details.
- [ ] Audit generation card to prevent cherry-picking of favorable random seeds or filtered samples.
- [ ] Clarify zero-shot criteria (data usage during pre-training, fine-tuning, or adaptation).

---

### 2. Data Provenance & Leakage Audit

**Principle**: Physical isolation among pre-training corpora, fine-tuning datasets, and independent test sets must be explicitly reported to ensure zero/few-shot capabilities are authentic and not artifacts of data contamination.

**Key Requirements:**
- **Strict Data Partitioning**: Mandate data splitting at the patient/donor level (not cell level); assign all longitudinal time points from one individual to a single split.
- **Cohort Disclosure**: Detail origins, platforms, temporal coverage, missingness mechanisms, and provide a per-modality "missingness map".
- **Overlap Audit**: Provide evidence of strict Train/Validation/Test physical isolation (e.g., Jaccard similarity of IDs, hash checks).

**Implementation Checklist:**
- [ ] Document cohort origins, platforms, temporal coverage, and provide a per-modality "missingness map".
- [ ] Strictly partition data at the patient/donor level, ensuring all longitudinal time points from one individual are in a single split.
- [ ] Audit for overlap using exact evidence (e.g., Jaccard similarity of IDs, hash checks).
- [ ] Check for implicit bias (over-reliance on a single center or sequencing platform) and data leakage.

---

### 3. Baseline & Shortcut Audit

**Principle**: Generative models must be benchmarked against robust non-generative baselines to conclusively demonstrate genuine learning of complex biological manifolds, rather than merely fitting superficial clinical confounders.

**Key Requirements:**
- **Baseline Comparison**: Compare end-to-end against non-generative baselines (specifically KNN, mean imputation, PCA); report performance delta (Δ).
- **Shortcut Ablation**: Re-evaluate performance after splitting by center or permuting technical covariates (e.g., batch, platform labels) to test confounder dependence.
- **Distribution Matching**: Report global mixing metrics (e.g., Wasserstein distance, MMD, LISI) as a sanity check.

**Implementation Checklist:**
- [ ] Compare end-to-end against non-generative baselines (KNN, mean imputation, or PCA) and report performance delta (Δ).
- [ ] Re-evaluate performance by permuting technical covariates to test confounder dependence (Shortcut ablation).
- [ ] Report global mixing metrics (e.g., Wasserstein distance, MMD, LISI) as a sanity check.
- [ ] Audit for shortcut learning, posterior collapse, or Occam's razor failure.

---

### 4. Uncertainty Quantification & Boundary Reporting

**Principle**: The model must explicitly delineate out-of-distribution (OOD) or low-confidence generation boundaries. Quantifying epistemic and aleatoric uncertainty is as important as the point estimates themselves.

**Key Requirements:**
- **Stratified Metrics**: Report performance stratified by center, key clinical/cell subpopulations, and feature frequency (e.g., common vs. rare features).
- **Calibration**: Report Expected Calibration Error (ECE), predictive variance, or latent-space entropy across subgroups.
- **OOD Extrapolation**: Evaluate performance and calibration drift (e.g., AUROC/ECE shift) on ≥ 1 external cohort.

**Implementation Checklist:**
- [ ] Report performance stratified by center, key clinical/cell subpopulations, and feature frequency.
- [ ] Output confidence intervals or report Expected Calibration Error (ECE), predictive variance, or latent-space entropy across subgroups.
- [ ] Delineate explicit out-of-distribution (OOD) or low-confidence generation boundaries.
- [ ] Evaluate calibration drift (e.g., AUROC/ECE shift) on ≥ 1 external cohort.

---

### 5. Downstream Biological Validity

**Principle**: Evaluation metrics must never be limited to mathematical reconstruction errors (like MSE). They must encompass the concordance and biological self-consistency of the generated data in downstream tasks.

**Key Requirements:**
- **DE Consistency**: Compare generated vs. real differentially expressed (DE) gene lists using rank correlation or Jaccard index, with special attention to non-trivial DEGs and clinically relevant pathways.
- **Topological Consistency**: Assess global structure and local neighborhoods using ARI, NMI, or manifold visualization (e.g., UMAP/Seurat).
- **Clinical Empirical Loop**: Validate ≥ 1 downstream task on held-out paired empirical measurements (e.g., survival C-index).

**Implementation Checklist:**
- [ ] Validate downstream biological tasks beyond mathematical reconstruction errors (MSE, Pearson r).
- [ ] Evaluate differential expression (DE) consistency using rank correlation or Jaccard index.
- [ ] Assess topological consistency (e.g., using ARI, NMI, or UMAP/Seurat).
- [ ] Validate at least one clinical empirical loop (e.g., survival C-index) on held-out paired data.
- [ ] Check for signal dilution (over-smoothing of rare subpopulations) and ghost samples (biologically incoherent profiles).

---

### 6. Open Science & Living Guidelines

**Principle**: Transparency in model weights, hyperparameters, and random seeds is the cornerstone of trust. Authors must provide complete environments and reproducible demos.

**Key Requirements:**
- **Code & Environment**: Release complete preprocessing, training, and inference scripts with Docker/Conda specifications.
- **Minimal Reproducible Design**: Provide a cloud-executable demo (e.g., Colab) and a lightweight toy dataset (≤ 10 min execution).
- **Weight Disclosure**: Provide pre-trained model weights.

**Implementation Checklist:**
- [ ] Release complete source code, preprocessing, training, and inference scripts.
- [ ] Provide Docker/Singularity container or Conda environment specifications.
- [ ] Provide a cloud-executable demo (e.g., Colab) and a lightweight toy dataset (≤ 10 min execution).
- [ ] Release pre-trained model weights.
- [ ] Document all hyperparameters and random seeds in configuration files.

---


## MIGOE Checklist

📥 **[Download MIGOE Checklist (Word Document)](assets/MIGOE-checklist.docx)**

The following table summarizes the six core principles with evaluation objectives, minimum reporting requirements, and common failure modes. You can also download the checklist as a Word document for easy reference and self-assessment.


| Core Dimension | Evaluation Objective | Minimum Reporting & Metrics | Common Failure Modes |
|----------------|---------------------|----------------------------|---------------------|
| **1. Tier Alignment & Generation Card** | Align capabilities with claims; ensure auditable generation. | • **Tier declaration**: Specify target Tier (0–4) with a concise rationale based on task complexity and data modalities.<br>• **Zero-shot criteria**: Specify if target-cohort or target-modality paired data were used during pre-training, fine-tuning, or adaptation.<br>• **Generation card**: Disclose output type (point estimates vs. sampled distributions), sampling frequency, random seed strategy, and post-processing/QC rules. | • **Tier mismatch**: Using lower-tier evidence for higher-tier claims<br>• **Cherry-picking**: Selectively reporting favorable random seeds or filtered samples to inflate performance. | 
| **2. Data Provenance & Leakage Audit** | Define in-domain boundaries; prevent test set contamination. | • **Cohort disclosure**: Detail cohort origins, sequencing platforms, temporal coverage, and missingness mechanisms; provide a per-modality "missingness map".<br>• **Strict isolation**: Mandate data splitting at the patient/donor level (not cell level); assign all longitudinal time points from one individual to a single split.<br>• **Overlap audit**: Provide evidence of strict Train/Validation/Test physical isolation (e.g., Jaccard similarity of IDs, hash checks). | • **Implicit bias**: Over-reliance on single center/platform<br>• **Data leakage**: (Improper splitting allows test distribution visibility via cell-level random splitting (donor overlap) or inclusion of future time-point samples. |
| **3. Baseline & Shortcut Audit** | Prevent learning technical noise; justify generative architecture complexity. | • **Shortcut ablation**: Re-evaluate performance after splitting by center or permuting technical covariates (e.g., batch, platform labels) to test confounder dependence.<br>• **Baseline comparison**: Compare end-to-end against non-generative baselines (e.g., KNN, mean imputation, PCA); report performance delta (Δ).<br>• **Distribution matching**: Report global mixing metrics (e.g., Wasserstein distance, MMD, LISI) as a sanity check. | • **Shortcut learning**: The model predominantly memorizes batch effects or clinical covariates instead of underlying biological mechanisms.<br>• **Posterior collapse**: Ignoring latent variables, degenerating into a simplistic mean output.<br>• **Occam's razor failure**: Added complexity is unjustified as simple baselines perform comparably. |
| **4. Uncertainty Quantification & Boundary Reporting** | Establish trust boundaries; prevent mean performance from masking long-tail failures.| • **Stratified metrics**: Report performance stratified by center, key clinical/cell subpopulations, and feature frequency (e.g., common vs. rare cell types/genes).<br>• **Calibration**: Report Expected Calibration Error (ECE), predictive variance, or latent-space entropy across subgroups.<br>• **OOD extrapolation**: Evaluate performance and calibration drift (e.g., AUROC/ECE shift) on ≥ 1 external cohort. | • **Overconfidence**: Assigning high confidence to completely unseen or anomalous samples.<br>• **Long-tail collapse**: Strong average metrics masking severe degradation on rare, clinically critical subpopulations. |
| **5. Downstream Biological Validity** | Move from "looking similar" to "being biologically useful"; verify biological logical consistency and downstream task relevance. | • **DE consistency**: Compare generated vs. real differentially expressed (DE) gene lists using rank correlation or Jaccard index, with special attention to non‑trivial DEGs and clinically relevant pathways.<br>• **Topological consistency**: Assess global structure and local neighborhoods using ARI, NMI, or manifold visualization (e.g., UMAP/Seurat).<br>• **Clinical loop**: Validate ≥ 1 downstream task on held-out paired empirical measurements (e.g., survival C-index). | • **Signal dilution**: Over-smoothing to minimize global MSE, erasing distinctive signals of rare subpopulations.<br>• **Ghost samples**: Generating biologically incoherent profiles where mutually exclusive genes are highly co-expressed. |
| **6. Open Science & Living Guidelines** | Ensure independent verification; build trust in AI-driven biology. | • **Code & environment**: Release complete preprocessing, training, and inference scripts with Docker/Conda specifications.<br>• **Minimal reproducible design**: Provide a cloud-executable demo (e.g., Colab) and a lightweight toy dataset (≤ 10 min execution).<br>• **Weight disclosure**: Provide pre-trained model weights.<br>• **Ethics**: State IRB approvals, data-use agreements, and re-identification risk assessments for generated data. | • **Environment dependency**: "Works on my machine"; fails elsewhere due to version conflicts.<br>• **Hyperparameter black box**: Undisclosed key coefficients or noise schedules preventing robust reproduction. |

---

## Compliance Levels

### Minimum Compliance (Required)
- Address all 6 principles
- Complete all "must" requirements
- Provide basic documentation

### Recommended Compliance
- Complete all implementation checklists
- Provide detailed supplementary materials
- Engage with community feedback

### Exemplary Compliance
- Exceed minimum requirements
- Contribute case studies to the community
- Participate in framework evolution

---

## Quick Start

### For Researchers
1. Review the six core principles above
2. Use the implementation checklists to evaluate your model
3. Prepare Generation Card and documentation
4. Ensure compliance before publication

### For Reviewers
1. Use MIGOE principles as a systematic review checklist
2. Verify Generation Card completeness (Principle 1)
3. Audit data partitioning (Principle 2)
4. Check baseline comparisons (Principle 3)
5. Assess uncertainty quantification (Principle 4)
6. Evaluate biological validity (Principle 5)
7. Confirm reproducibility (Principle 6)

### For Contributors
We welcome community contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for:
- How to suggest improvements
- Literature additions
- Case study submissions
- Issue reporting

---

## Citation

If you use the MIGOE framework in your research, please cite:

```bibtex
@misc{migoe2026,
  title={MIGOE: Minimum Information for Generative Omics Evaluation},
  author={[Li-OmicsLab-MPU Team]},
  year={2026},
  howpublished={\url{https://github.com/Li-OmicsLab-MPU/MIGOE-Checklist}},
  note={A framework for establishing trust boundaries in generative omics}
}
```

---

## License

This project is licensed under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](LICENSE).

You are free to:
- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material for any purpose

Under the following terms:
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made

---

## Contact

- **Issues**: [GitHub Issues](../../issues)
- **Discussions**: [GitHub Discussions](../../discussions)
- **Email**: kefengl@mpu.edu.mo

---

## Acknowledgments

We thank all researchers, reviewers, and community members who contribute to the MIGOE framework.

---

**Version**: 1.0  
**Last Updated**: March 2026  
**Status**: Living Document - Open for Community Feedback
