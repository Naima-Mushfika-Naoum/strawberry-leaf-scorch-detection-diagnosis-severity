# Semantic Analysis of Strawberry Leaf Scorch

### Disease detection · Symptom diagnosis · Severity prediction

Research code and pretrained model artifacts accompanying:

**Semantic Analysis of Strawberry Leaf Scorch for Disease Detection, Symptom Diagnosis, and Severity Prediction**  
Naima Mushfika and Emad Sami Jaha  
*International Journal of Computational Intelligence Systems*, **19**, article 368 (2026)

[Read the paper](https://doi.org/10.1007/s44196-026-01458-x) · [Execution guide](docs/EXECUTION.md) · [Model details](models/README.md) · [Data availability](docs/DATA_AVAILABILITY.md) · [Citation](#citation)

## Overview

This repository provides research notebooks for strawberry leaf scorch analysis: spot-distribution classification, texture classification using GLCM features, and integrated disease, symptom, and severity analysis.

The supplied pretrained artifacts support the disease detector, spot classifier, and texture classifier. The curated dataset and annotations are **not publicly distributed in this repository**. This release organizes the supplied research code; it does not establish independent reproduction of the paper's results.

## Repository contents

| Location | Contents |
|---|---|
| `notebooks/01_spot_distribution.ipynb` | InceptionV3 spot-pattern training and inference experiments |
| `notebooks/02_texture_classification.ipynb` | GLCM feature analysis, SVM, random forest, and PCA experiments |
| `notebooks/03_disease_symptoms_severity.ipynb` | Integrated disease detection, symptom analysis, voting, and evaluation |
| `models/` | Model documentation, checksums, and location for locally extracted weights |
| `data/` | Input-layout instructions; no study data |
| `docs/` | Execution, data-access, validation, and review notes |
| `CITATION.cff` / `citation.bib` | Paper citation metadata |

## Pretrained models

Download `pretrained_models.zip` from this repository's **Releases** section after the model asset has been uploaded. Extract it into the repository root. The archive already contains the `models/` folder; do not extract it inside another `models/` directory.

| Artifact | Location after extraction |
|---|---|
| Disease detector | `models/Clean_Reviwers_DisDetect_best_final_model.h5` |
| Spot-distribution model | `models/Spots_Distribution_best_model_overall.h5` |
| Texture scaler | `models/SVM_PCA_GLCM/NG_scaler.joblib` |
| Texture classifier | `models/SVM_PCA_GLCM/NG_random_forest_model.joblib` |

The model files are distributed as a Release asset rather than ordinary repository files. Use the SHA-256 values in `models/model_manifest.json` to verify the downloads.

## Setup and use

1. Download or clone this repository.
2. Download and extract the model archive as described above.
3. Create an isolated Python environment. Install the dependencies listed in `requirements.txt` after reading the compatibility notes below.
4. Launch Jupyter from the repository root with `jupyter lab`.
5. Open the relevant notebook and set `PROJECT_ROOT` in its first code cell. All data and model paths derive from this location.
6. Supply your own appropriately prepared inputs or request the study subsets. Follow [the execution guide](docs/EXECUTION.md) to select an experiment.

The notebooks retain alternative experimental blocks and are not intended for an indiscriminate **Run all**. Notebook 03 loads pretrained models; the first two notebooks include training experiments and require private images or feature tables. The disease-detector training notebook is not included.

### Environment compatibility

The spot model records **Keras 2.15.0**, while the disease detector records **Keras 3.10.0**. The texture scaler and random forest record **scikit-learn 1.6.1**. A single environment that loads and runs all four artifacts has not yet been verified. `requirements.txt` is a dependency inventory, not a tested environment lock.

## Data availability

The study used strawberry images from the publicly available [PlantifyDr dataset](https://www.kaggle.com/datasets/lavaman151/plantifydr-dataset). The curated and annotated study subsets are not included here. Access may be requested by emailing **naoum1496@gmail.com**, identifying the paper and the subset required. Requests are considered upon reasonable request.

Downloading PlantifyDr does not provide the exact curated subsets or study annotations. See [data availability](docs/DATA_AVAILABILITY.md) for details.

## Citation

**If you use this code, the pretrained models, or the methodology in your research, please cite the associated paper:**

> Mushfika, N., & Jaha, E. S. (2026). Semantic Analysis of Strawberry Leaf Scorch for Disease Detection, Symptom Diagnosis, and Severity Prediction. *International Journal of Computational Intelligence Systems*, 19, 368. https://doi.org/10.1007/s44196-026-01458-x

```bibtex
@article{mushfika2026semantic,
  author = {Mushfika, Naima and Jaha, Emad Sami},
  title = {Semantic Analysis of Strawberry Leaf Scorch for Disease Detection, Symptom Diagnosis, and Severity Prediction},
  journal = {International Journal of Computational Intelligence Systems},
  volume = {19},
  pages = {368},
  year = {2026},
  doi = {10.1007/s44196-026-01458-x},
  url = {https://doi.org/10.1007/s44196-026-01458-x}
}
```

`CITATION.cff` supplies GitHub's citation metadata. Please also acknowledge the original dataset when using its images.

## Validation and limitations

Notebook structure and Python syntax were checked; saved outputs were removed. Model checksums and HDF5 configuration metadata were inspected. The texture artifacts loaded for inspection, with warnings about the installed scikit-learn version. No end-to-end predictions or published metrics were reproduced.

Existing issues involving alternative voting helpers, preprocessing, and evaluation are documented in [review notes](docs/REVIEW_NOTES.md). They have not been silently changed. Check those notes before claiming that a selected notebook variant reproduces the published experiment.



