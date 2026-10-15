# Lumbar-MRI-Segmentation-Failure-Analysis
Failure and quantitative analysis of nnU-Net segmentation of lumbar vertebrae and intervertebral discs in MRI, including evaluation metrics, structure-level analysis, field-of-view assessment, and Pfirrmann-grade subgroup analysis. 
# Lumbar MRI Segmentation Reproducibility Workflow

This repository contains notebooks for preparing the SPIDER dataset, running nnU-Net v2 inference, evaluating structure-level segmentation metrics, and analysing Dice-score distributions.

## Repository structure

- `01_dataset_preparation/prepare_spider_dataset.ipynb` — dataset preparation, label mapping, and nnU-Net dataset configuration.
- `02_prediction/foldwise_nnunet_prediction.ipynb` — fold-wise prediction, structure-level Dice calculation, and optional post-processing.
- `03_evaluation/structure_metrics_and_metadata_analysis.ipynb` — structure-level distance metrics and metadata analyses.
- `04_failure_analysis/dice_threshold_and_structure_analysis.ipynb` — Dice-threshold and structure-level distribution analyses.

## Configure paths and fold

Before running, update `/path/to/nnunet` and `/path/to/your/data` to locations on your system. The prediction notebook uses a single integer variable, `n`, to select a fold. For example, `n = 4` refers to fold 4, while the directory paths are constructed generically as `groundtruth_fold{n}` and `predictions_fold{n}`.

## Suggested execution order

1. Prepare the dataset and ensure the nnU-Net dataset configuration is valid.
2. Run the prediction notebook after selecting the desired fold and ensuring its validation cases and ground-truth labels are available.
3. Run the evaluation notebook using the appropriate prediction/reference paths and required metadata files.
4. Run the Dice-threshold and structure-level analyses using the resulting metrics table.

## Dependencies

The notebooks use Python packages including NumPy, pandas, SciPy, scikit-learn, Matplotlib, SimpleITK, nibabel, MedPy, openpyxl, and nnU-Net v2. See `requirements.txt` and `ENVIRONMENT.md`; install a PyTorch/CUDA combination compatible with the target machine for GPU inference.

## Reproducibility and data privacy

These notebooks have been cleaned for public sharing, but have not been executed end-to-end in a clean environment as part of packaging. Confirm data paths, label mappings, fold assignments, package compatibility, and input filenames before running. Do not commit patient MRI volumes, segmentation masks, restricted metadata, model weights, credentials, or other private data.
