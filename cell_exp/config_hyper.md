---
sort: 2
---

# Configuration

This table shows the implementation configuration and model hyperparameters.

| Name          | Choice            | Name            | Choice |
|---------------|-------------------|-----------------|--------|
| OS            | Unbuntu 20.04     | Frame Length, L | 16     |
| GPU           | NVIDIA GTX 1080Ti | Temporal Dim, t | 4      |
| Framework     | PyTorch           | Learning Rate   | 1e-6   |
| Batch Size    | 80                | Optimizer       | Adam   |
| Epoch         | 30                | Scheduler       | Cyclic |
| Loss          | HP Loss           |                 |        |

This table displays the evaluation metrics.

| Name     | Name     | Name  | Name        | Name        |
|----------|----------|-------|-------------|-------------|
| Accuracy | F1 Score | AUROC | Sensitivity | Specificity |

