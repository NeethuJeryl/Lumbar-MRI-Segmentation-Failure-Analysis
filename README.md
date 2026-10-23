# Lumbar MRI segmentation analysis notebooks

These notebooks are cleaned copies of the original analysis notebooks. The original calculation cells and analysis order have been preserved; personal absolute paths have been replaced with project-relative paths. Saved notebook outputs were cleared so the analyses regenerate outputs when run.

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

## Important

These are path-cleaned copies, not newly validated analyses. Run each notebook from top to bottom in the intended environment and verify file matching and results. The original calculation logic has not been rewritten. In particular, the HD95/ASD notebook should be checked against the metric definition and spacing policy described in the manuscript before treating its outputs as final.
