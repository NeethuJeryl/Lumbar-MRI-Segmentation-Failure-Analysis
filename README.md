# Lumbar MRI segmentation analysis

This workflow is for evaluating nnU-Net v2 segmentation of lumbar vertebrae and intervertebral discs in T2-weighted MRI. It includes dataset preparation, label mapping, model prediction, structure-specific evaluation, and analysis of segmentation performance and failure patterns. Evaluation uses metrics such as the Dice similarity coefficient (DSC), 95th-percentile Hausdorff distance (HD95), and average surface distance (ASD). Additional analyses examine performance across anatomical levels, intervertebral disc degeneration grades, and field-of-view conditions. The repository is intended to support transparent, analysis of segmentation results and systematic investigation of model errors.

## Folder layout

```text
repository-root/
├── data/
│   ├── Original_dice_all_fold.xlsx
│   ├── masks/                         # reference masks, if needed
│   ├── predictions/                   # predictions, if needed
│   └── radiological_gradings.csv      # Pfirrmann metadata
├── outputs/                           # generated CSVs and figures
└── analysis/
    ├── 01_fov_analysis.ipynb
    ├── 02_individual_structure_hd95_assd.ipynb
    ├── 03_overall_performance.ipynb
    ├── 04_sensitivity_and_threshold_free_distributions.ipynb
    └── 05_pfirrmann_subgroup_analysis.ipynb
```

Move the notebooks into the `analysis/` folder or adjust the relative paths if running them from another working directory. The notebooks expect inputs to be available locally; data and predictions are not included in this repository. Create `outputs/` before running notebooks that save files.

Label Mapping

The original segmentation labels were mapped to consecutive integer labels for compatibility with the nnU-Net v2 training pipeline. The intervertebral disc labels were remapped as follows: 201 → 6 (L5–S1), 202 → 7 (L4–L5), 203 → 8 (L3–L4), 204 → 9 (L2–L3), 205 → 10 (L1–L2), and 206 → 11 (T12–L1). The vertebral labels were retained as labels 1–5, corresponding to L5, L4, L3, L2, and L1, respectively. Background was represented by label 0, and the spinal canal label (100) was converted to background (0). This mapping provided a consistent label representation for dataset preparation and model training.
