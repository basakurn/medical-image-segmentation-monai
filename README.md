# Medical Image Segmentation with MONAI

This project presents an end-to-end **medical image segmentation pipeline** using **MONAI** and **PyTorch**, demonstrated on hippocampal MRI data.
The focus of this work is not only on model training, but also on building a clear, reproducible pipeline and evaluating results both quantitatively and qualitatively.

## Project Overview

The pipeline covers the following stages:

- Loading and preprocessing 3D medical images
- Applying MONAI-based transform pipelines
- Training a segmentation model
- Evaluating performance using Dice score
- Visualizing predictions against ground truth masks

## Dataset & Preprocessing

Input data consists of 3D medical images (MRI volumes) and corresponding segmentation labels.
Data is split into training and validation sets.
Preprocessing and augmentation are implemented using MONAI transforms, with training data including random flips and rotations for data augmentation.

## Model & Training Setup

- **Model**: 3D U-Net architecture provided by MONAI
- **Loss Function**: Dice loss 
- **Optimizer**: Adam
- **Training**:
  - Supervised learning
  - Mini-batch training (batch_size=1)
  - Number of epochs: 6
 
Validation performed every 2 epochs using Dice metric (excluding background) and model state with the highest validation Dice is saved as `best_metric_model.pth`.
The training loop is implemented explicitly to keep the process transparent and easy to modify.

## Evaluation

- **Metric**: Dice Score
Performance is evaluated on the validation set. In addition to numeric metrics, **qualitative visualizations** are used to assess segmentation quality.

While the current results demonstrate a working pipeline, there is clear room for improvement in model performance.

## Results & Visualization

Sample visualizations include:

- Input image slices
- Ground truth segmentation
- Model predictions

These visual comparisons help interpret model behavior beyond aggregate metrics.

## Known Limitations

- Hyperparameter tuning was limited and not exhaustive.
- Training was done for a small number of epochs and with limited compute resources.
- Model performance is sensitive to preprocessing and data augmentation choices.

## Next Steps

Potential improvements for this pipeline include:

- Fine-tuning data augmentation strategies
- Optimizing hyperparameters such as learning rate, channels, and num_res_units
- Applying post-processing techniques to improve segmentation quality
- Extending training schedules and incorporating learning rate scheduling
