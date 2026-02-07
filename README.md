## Research framing
This notebook is an experimental study of GAN training dynamics under different objectives and regularization settings.

### Research questions
- How do loss functions (non-saturating vs. hinge) affect stability and sample quality?
- Which training heuristics (label smoothing, noise injection, gradient penalty) reduce mode collapse?
- How sensitive are results to the update ratio (D:G steps) and learning rate schedules?

### Hypotheses
- H1: Hinge loss improves discriminator gradients early and stabilizes training.
- H2: Gradient penalty reduces exploding gradients and mitigates mode collapse.
- H3: Increasing D steps (e.g., 5:1) improves stability but may slow generator improvement.

### Method (high-level)
- Dataset: (MNIST/CIFAR-10/…)
- Architecture: baseline DCGAN-style (or your architecture)
- Optimization: Adam (lr=…, betas=…)
- Evaluation: FID/IS (if implemented) + qualitative samples + loss curves
