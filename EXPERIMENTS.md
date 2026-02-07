# Experiments Log (GAN)

## Environment
- Date: 2026-02-07
- Framework: (PyTorch / TensorFlow) 
- Device: CPU / GPU (CUDA)
- Python: 3.10+
- Seed: 42
- Notebook: gan.ipynb

---

## E0 — Baseline (DCGAN-style)
**Goal:** establish a stable baseline run and reference samples.

- Dataset: MNIST (28x28, grayscale)  ← change if not MNIST
- Preprocessing:
  - Normalize to [-1, 1]
  - Batch shuffle = True
- Model:
  - Generator: latent_dim = 100, DCGAN-like upsampling blocks
  - Discriminator: DCGAN-like conv blocks + LeakyReLU
- Loss: Non-saturating GAN (BCEWithLogits)
- Optimizer: Adam
  - lr_G = 2e-4
  - lr_D = 2e-4
  - betas = (0.5, 0.999)
- Training:
  - epochs = 100
  - batch_size = 128
  - D:G update ratio = 1:1
  - label smoothing = off
  - gradient penalty = off
  - dropout = off
- Logging:
  - Save samples every 5 epochs
  - Save checkpoint every 20 epochs
  - Track losses: L_D, L_G

**Observations:**
- Expected: L_D and L_G oscillate; samples improve gradually.
- Watch for: mode collapse (same digit repeated), D dominating (L_G exploding).

**Result summary (fill after run):**
- Best visual quality epoch: __
- Failure signs: __
- Notes: __

---

## E1 — Label smoothing (stability test)
**Change vs E0:**
- Real labels = 0.9 instead of 1.0 (one-sided label smoothing)

**Hypothesis:**
- Less overconfident discriminator → smoother gradients → fewer collapses.

**Settings:**
- Same as E0
- epochs = 100
- batch_size = 128

**Result summary:**
- Compare to E0: sample diversity __, stability __

---

## E2 — Noise injection to discriminator (regularization)
**Change vs E0:**
- Add Gaussian noise to inputs of D: std = 0.05 (or 0.1 if needed)

**Hypothesis:**
- Regularizes D and reduces overfitting, improves G learning signal.

**Settings:**
- Same as E0
- epochs = 100

**Result summary:**
- Compare to E0: __

---

## E3 — Update ratio (D stronger)
**Change vs E0:**
- D:G update ratio = 5:1 (five discriminator steps per generator step)

**Hypothesis:**
- Stronger D early can stabilize training, but may slow G progress.

**Settings:**
- epochs = 100
- batch_size = 128
- lr same as E0 initially (adjust if D overwhelms)

**Result summary:**
- Compare to E0: __

---

## Planned evaluation (lightweight)
- Qualitative: sample grids at epochs 1, 10, 25, 50, 75, 100
- Curves: L_D and L_G
- Optional quantitative (later): FID (if you add it)
