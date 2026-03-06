# MIGOE: Minimum Information for Generative Omics Evaluation

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg)](CONTRIBUTING.md)

## Overview

The MIGOE (Minimum Information for Generative Omics Evaluation) framework establishes rigorous standards for evaluating generative AI models in omics research. It addresses critical challenges in establishing trust boundaries and audit standards for clinical artificial intelligence (ACI) deployment.

![MIGOE Framework Overview](assets/migoe-framework-overview.png)
*Figure 1: MIGOE Framework Overview. The framework evaluates generative omics models across six core dimensions, from data input through latent alignment to establishing trust boundaries for safe clinical deployment.*

## Core Values

- **Trust Boundary Definition**: Clearly define the capability scope and limitations of generative omics models
- **Audit Standards**: Provide repeatable and verifiable evaluation methodologies
- **Clinical Translation Support**: Ensure quality assurance for ACI system deployment
- **Community-Driven Updates**: Continuously integrate latest research and best practices

## Target Audience

- Multi-omics data scientists and bioinformaticians
- Generative AI model developers
- Clinical metabolomics researchers
- Medical AI regulators and auditors
- Precision medicine and translational medicine practitioners

---

## Six Core Principles

The framework strictly requires adherence to the following six core principles:

### 1. Tier Alignment & Generation Card

**Principle**: Model evaluation must be strictly aligned with its claimed maturity tier to prevent using evidence from lower tiers to support higher-tier generalization claims.

**Key Requirements:**
- **Generation Card Disclosure**: Document all sampling iterations, random seed strategies, and post-processing filtering rules
- **Tier Declaration**: Specify target tier with rationale
- **Zero-shot Criteria**: Clarify data usage during pre-training, fine-tuning, or adaptation

**Implementation Checklist:**
- [ ] Document all random seeds used (not just the "best" one)
- [ ] Report the number of generation attempts
- [ ] Disclose any post-hoc filtering or selection criteria
- [ ] Align evaluation metrics with the claimed maturity tier
- [ ] Provide statistical distribution of results across multiple runs

---

### 2. Data Provenance & Leakage Audit

**Principle**: Authors must explicitly report the physical isolation among pre-training corpora, fine-tuning datasets, and independent test sets.

**Key Requirements:**
- **Strict Data Partitioning**: Partition at the patient/donor level (not cell level)
- **Cohort Disclosure**: Detail origins, platforms, temporal coverage, and missingness mechanisms
- **Overlap Audit**: Provide evidence of strict Train/Validation/Test isolation

**Implementation Checklist:**
- [ ] Document complete data provenance (source, collection date, processing pipeline)
- [ ] Verify patient/donor-level splitting for omics data
- [ ] Audit for sample overlaps between train/validation/test sets
- [ ] Check for shared biological covariates (e.g., batch effects, sequencing platform)
- [ ] Identify and report any technical confounders
- [ ] Provide data partition statistics (number of unique patients/donors per split)

---

### 3. Baseline & Shortcut Audit

**Principle**: Generative models must be benchmarked against robust non-generative baselines to conclusively demonstrate genuine learning of complex biological manifolds.

**Key Requirements:**
- **Mandatory Baseline Comparisons**: Compare against KNN, mean imputation, PCA, linear regression
- **Shortcut Ablation**: Test confounder dependence by permuting technical covariates
- **Distribution Matching**: Report global mixing metrics (Wasserstein distance, MMD, LISI)

**Implementation Checklist:**
- [ ] Implement at least 3 non-generative baseline methods
- [ ] Report baseline performance using identical evaluation metrics
- [ ] Conduct statistical significance tests (e.g., paired t-test, Wilcoxon)
- [ ] Analyze where the generative model outperforms/underperforms baselines
- [ ] Justify computational cost vs. performance gain
- [ ] Test for shortcut learning (e.g., does the model rely on batch effects?)

---

### 4. Uncertainty Quantification & Boundary Reporting

**Principle**: The model must output confidence intervals or calibration metrics for generated features, explicitly delineating out-of-distribution (OOD) or low-confidence generation boundaries.

**Key Requirements:**
- **Uncertainty Metrics**: Confidence intervals, ECE, epistemic and aleatoric uncertainty
- **Stratified Metrics**: Report performance by center, subpopulations, and feature frequency
- **OOD Extrapolation**: Evaluate calibration drift on external cohorts

**Implementation Checklist:**
- [ ] Provide confidence intervals or credible intervals for generated features
- [ ] Report Expected Calibration Error (ECE)
- [ ] Implement OOD detection mechanism
- [ ] Distinguish epistemic vs. aleatoric uncertainty
- [ ] Visualize uncertainty distributions
- [ ] Define explicit boundaries where predictions should not be trusted
- [ ] Validate calibration on held-out data

---

### 5. Downstream Biological Validity

**Principle**: Evaluation metrics must never be limited to mathematical reconstruction errors. They must encompass biological consistency and validity in downstream tasks.

**Key Requirements:**
- **Beyond Reconstruction**: Evaluate differential expression, cell clustering, survival prediction
- **DE Consistency**: Compare generated vs. real DE gene lists
- **Topological Consistency**: Assess structure using ARI, NMI, manifold visualization
- **Clinical Empirical Loop**: Validate on held-out paired measurements

**Implementation Checklist:**
- [ ] Report standard reconstruction metrics (MSE, Pearson r, etc.)
- [ ] Evaluate on at least 2 downstream biological tasks
- [ ] Test preservation of rare biological signals
- [ ] Validate known biological relationships (e.g., gene-gene correlations)
- [ ] Compare downstream task performance: real vs. generated data
- [ ] Assess biological plausibility with domain experts
- [ ] Check for preservation of data structure (e.g., manifold topology)

---

### 6. Open Science & Living Guidelines

**Principle**: Authors must provide complete source code, environmental containers, and minimally reproducible demos to ensure independent verification.

**Key Requirements:**
- **Code & Environment**: Release complete scripts with Docker/Conda specifications
- **Minimal Reproducible Design**: Provide cloud-executable demo (< 10 min runtime)
- **Weight Disclosure**: Provide pre-trained model weights
- **Ethics & Privacy**: State IRB approvals and re-identification risk assessments

**Implementation Checklist:**
- [ ] Publish code on public repository (GitHub, GitLab, etc.)
- [ ] Provide Docker/Singularity container or detailed environment specification
- [ ] Release model weights (or provide access mechanism)
- [ ] Document all hyperparameters in configuration files
- [ ] Include random seeds in code and documentation
- [ ] Create minimal working example (< 100MB data, < 10 min runtime)
- [ ] Provide step-by-step reproduction instructions
- [ ] Specify software versions and dependencies
- [ ] Include unit tests or validation scripts

---

## Summary Table

| Core Dimension | Evaluation Objective | Minimum Reporting & Metrics | Common Failure Modes |
|----------------|---------------------|----------------------------|---------------------|
| **1. Tier Alignment & Generation Card** | Align capabilities with claims; ensure auditable generation. | • **Tier declaration**: Specify target Tier (0–4) with rationale<br>• **Zero-shot criteria**: Specify data usage during training<br>• **Generation card**: Disclose sampling, seeds, post-processing | • **Tier mismatch**: Using lower-tier evidence for higher-tier claims<br>• **Cherry-picking**: Selective reporting of favorable results |
| **2. Data Provenance & Leakage Audit** | Define in-domain boundaries; prevent test set contamination. | • **Cohort disclosure**: Detail origins, platforms, missingness<br>• **Strict isolation**: Patient/donor-level splitting<br>• **Overlap audit**: Evidence of Train/Val/Test isolation | • **Implicit bias**: Over-reliance on single center/platform<br>• **Data leakage**: Cell-level splitting or temporal contamination |
| **3. Baseline & Shortcut Audit** | Prevent learning technical noise; justify complexity. | • **Shortcut ablation**: Test confounder dependence<br>• **Baseline comparison**: Compare against simple methods<br>• **Distribution matching**: Report mixing metrics | • **Shortcut learning**: Memorizing batch effects<br>• **Posterior collapse**: Degenerating to mean output<br>• **Occam's razor failure**: Unjustified complexity |
| **4. Uncertainty Quantification** | Establish trust boundaries; prevent masking failures. | • **Stratified metrics**: By center, subpopulations, features<br>• **Calibration**: ECE, predictive variance<br>• **OOD extrapolation**: External cohort evaluation | • **Overconfidence**: High confidence on anomalies<br>• **Long-tail collapse**: Average metrics masking rare failures |
| **5. Downstream Biological Validity** | Move from "looking similar" to "being useful". | • **DE consistency**: Compare gene lists<br>• **Topological consistency**: ARI, NMI, manifold<br>• **Clinical loop**: Validate on paired measurements | • **Signal dilution**: Over-smoothing erases rare signals<br>• **Ghost samples**: Biologically incoherent profiles |
| **6. Open Science & Living Guidelines** | Ensure independent verification; build trust. | • **Code & environment**: Complete scripts, containers<br>• **Reproducible demo**: Cloud-executable, < 10 min<br>• **Weight disclosure**: Pre-trained models<br>• **Ethics**: IRB, privacy assessments | • **Environment dependency**: Version conflicts<br>• **Hyperparameter black box**: Undisclosed settings<br>• **Privacy risk**: Re-identification risks |

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
  author={[Author Team]},
  year={2026},
  howpublished={\url{https://github.com/[username]/MIGOE}},
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
- **Email**: [project-email@example.com]

---

## Acknowledgments

We thank all researchers, reviewers, and community members who contribute to the MIGOE framework.

---

**Version**: 1.0  
**Last Updated**: March 2026  
**Status**: Living Document - Open for Community Feedback
