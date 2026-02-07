## SOM (Self-Organizing Map) — research notebook

### Goal
Explore unsupervised representation learning using a Self-Organizing Map (Kohonen network) for dimensionality reduction and clustering.

### Research questions
- How do map size and neighborhood radius affect topological preservation?
- What is the effect of learning rate schedule on convergence?
- How well does SOM separate classes/clusters compared to k-means/PCA (qualitatively or quantitatively)?

### Method
- Data: (your dataset here)
- Preprocessing: standardization / normalization
- SOM grid: (e.g., 20x20)
- Distance metric: Euclidean
- Neighborhood: Gaussian
- Training: 100 epochs (or iterations = N)

### Outputs
- Training curve (quantization error)
- U-Matrix visualization (optional)
- Cluster assignment / labeling (optional)

### Reproducibility
- Fixed seed: 42
- Saved plots and parameters for each run
