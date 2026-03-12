# Contributing to MIGOE

Thank you for your interest in contributing to the MIGOE (Minimum Information for Generative Omics Evaluation) framework. As a living guideline, MIGOE relies on ongoing community input. We welcome researchers, computational biologists, and clinical AI developers to help refine these standards.

## 1. Contribution Principles

To maintain the necessary academic rigor for clinical AI deployment, please ensure your contributions align with the following principles:
* **Academic Rigor**: All proposed changes, new metrics, or added failure modes must be supported by peer-reviewed literature or extensively validated practical experience.
* **Scope Consistency**: Contributions should focus on high-level methodology and evaluation principles rather than tool-specific tutorials.
* **Constructive Collaboration**: Maintain a professional and constructive tone in all Issues and Discussions.

## 2. How to Contribute

### A. Reporting Issues or Typos
If you find an error, an outdated reference, or unclear wording, please [open an Issue](../../issues). 
* Use a descriptive title (e.g., *Typo in Principle 3* or *Clarification needed for ECE metric*).
* Provide a brief explanation of the problem and your suggested fix.

### B. Adding Literature & References
Generative omics is evolving rapidly. To add a recent, high-impact paper that supports or expands upon one of the six principles:
1. Fork this repository.
2. Add the reference to the relevant section in `README.md` or `MIGOE-checklist.docx`.
3. Submit a Pull Request (PR) detailing why the paper strengthens the framework.

### C. Proposing Revisions to the Framework
For substantial changes (e.g., adding metrics, modifying Checklist requirements, or introducing a new Failure Mode):
1. **Discuss First**: [Open a Discussion](../../discussions) or Issue to propose the change before editing the document.
2. **Provide Evidence**: Include a clear rationale and relevant literature citations.
3. **Submit a PR**: Following the discussion, fork the repository, apply your edits, and submit a PR.

### D. Contributing Case Studies
We encourage researchers to share how they applied MIGOE in specific modalities (e.g., clinical metabolomics, single-cell RNA-seq, spatial transcriptomics).
* Submit a short summary via an Issue, or add a markdown file in a `case-studies/` directory via a PR.
* Highlight which principles were straightforward to apply, which required domain-specific adaptation, and key takeaways.

## 3. Pull Request (PR) Process

1. **Fork** the repository and clone it locally.
2. **Create a branch** for your edits (e.g., `git checkout -b update-principle-4`).
3. **Commit** your changes with clear, descriptive messages.
4. **Push** to your fork and submit a **Pull Request** to the `main` branch.
5. **Review**: Maintainers will review the PR and may request adjustments for clarity or consistency before merging.

## 4. Recognition

Significant contributors will be acknowledged in future updates and releases. We appreciate your efforts in helping make generative omics more trustworthy and auditable.

---

*For any questions, please use [GitHub Discussions](../../discussions) or contact the maintainer at kefengl@mpu.edu.mo.*
