# Execution guide

## Configure paths

Each notebook starts with the same configuration block. Set `PROJECT_ROOT` to the directory containing `data/`, `models/`, and `results/`. Alternatively set the `STRAWBERRY_PROJECT_ROOT` environment variable before starting Jupyter. Paths in scientific cells derive from these locations. Archive extraction and Colab-specific mounting commands have been removed: prepare your private inputs separately.

## Spot distribution

Run the imports, inventory, label collection and shared definitions first. Choose one training variant (A, B, or C). Later variants redefine the generator and may overwrite checkpoints. Plotting cells require histories produced by the selected variant. The single-image inference cell is optional and requires the named model file plus an image. The first variant's exported model filename differs from the inference filename; see `models/README.md`.

## Texture classification

Supply the three GLCM CSVs, then run assembly, inspection and feature preparation. The first split/scaling section feeds SVM and random-forest experiments. The tuned random-forest export is used by integrated inference. PCA/SVM sections are alternative experiments. Read the caveat before the final historical tuning block; it has preprocessing leakage and is not a validated evaluation path.

## Integrated analysis

Extract the supplied model archive to obtain the disease detector, spot classifier, texture scaler and random forest. Run imports and feature/helper definitions, then select an evaluation block. Repeated definitions of `process_images_in_folder` and `majority_voting_1` replace previous definitions. Start a fresh kernel and rerun prerequisites when switching variants. No single publication-generating variant has been asserted here.

Fold-summary and ablation blocks operate on stored predictions in memory, not freshly trained fold-specific models. Timing and per-stage routines are separate exploratory blocks with additional input assumptions.

## Environment and verification

`requirements.txt` lists observed dependencies only. The original Python and TensorFlow versions are unknown. Model metadata records Keras 2.15.0 for the spot classifier, Keras 3.10.0 for the disease detector, and scikit-learn 1.6.1 for the texture artifacts. Loading legacy models or running older imports may require the original environment. Record successful package versions before claiming reproducibility.

The release was checked for notebook validity, Python syntax, removed outputs and relocated paths. The texture artifacts were loaded for inspection with cross-version warnings. No training, neural-network loading, image inference or numerical reproduction was performed.
