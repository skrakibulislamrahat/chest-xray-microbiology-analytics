# Chest X-ray Microbiology Analytics

Reproducibility materials for the study *Cross-Dataset Reliability of Chest Radiograph Models: Provenance-Aware Analytics and Implications for Microbiology*.

The study compares four dataset-defined tasks—Kaggle/Kermany pneumonia, RSNA lung opacity, CheXpert pneumonia, and CheXpert lung opacity—without treating their labels as interchangeable. It reports discrimination, calibration, high-confidence errors, and source-validation-threshold flag volume. The microbiology connection is an interpretation boundary: the models were not trained to identify organisms, predict laboratory outcomes, or guide testing.

## Files

- [`paper_release/Full_research_analysis_patient_bootstrap.ipynb`](paper_release/Full_research_analysis_patient_bootstrap.ipynb): Google Colab notebook for analysis of saved per-image predictions.
- [`paper_release/data/`](paper_release/data/): aggregated result tables, split audit summary, and analysis manifest.
- [`paper_release/figures/`](paper_release/figures/): AUROC, AUPRC, ECE15, and threshold-flag heatmaps.
- [`paper_release/README.md`](paper_release/README.md): input file format and run instructions.

## Scope and reproduction

The notebook reproduces the post-training analysis. It does **not** train models or run image inference. To regenerate its result tables from scratch, a researcher needs lawful access to the original datasets and the five-seed model predictions and source-validation thresholds in the documented CSV formats. Raw images, model checkpoints, and per-image prediction files are not included in this repository. The published CSV files are aggregate task-level summaries.

Open the notebook in Colab, set its `PROJECT` path to a Drive folder containing the prediction and operating-point files, and run all cells. The notebook expects 16 source-target pairs, five seeds per pair, and uses 500 bootstrap replicates. It samples patients when identifiers are available and images otherwise; Kaggle/Kermany has no usable patient identifier in this project. Bootstrap intervals are conditional on the saved five-seed ensemble and do not estimate prospective or between-hospital performance.

See [`paper_release/README.md`](paper_release/README.md) for exact file names and required columns.

## Data and responsible use

The chest radiograph datasets must be obtained directly from their providers under each provider's terms. This repository does not redistribute them. The code and aggregate results are for research reproducibility and are not a clinical diagnostic system. No result here validates pathogen prediction or a microbiology-testing workflow.

## License

Code and documentation are provided under the MIT License. Dataset licenses and access conditions remain separate and must be followed.

