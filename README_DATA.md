# Private data location

No data are bundled. See [data availability](../docs/DATA_AVAILABILITY.md).

Expected directories depend on the selected notebook:

- `Spots_Distribution/`: `Clustered/`, `Scattered/`, `Speckled/`, `Varied/`.
- `All_Included_Final_Severity_Stage/`: stage-labelled images, retaining the exact label folder names expected by the supplied analysis code.
- `features/Non_Green_Region/`: `Early_Stage_glcm_features_with_labels.csv`, `Medium_Stage_glcm_features_with_labels.csv`, `Severe_Stage_glcm_features_with_labels.csv`.

Other exploratory routines use `Severity_Stage_Spots/Severity_Stage_Spots/`, `Severity_Stage_Labeling/`, and `Severity_Stage_Val/Medium_Stage/`. These are alternative study inputs, not automatically generated directories. Single-image examples require you to replace the example filename with an available local image.

The texture notebook writes merged CSVs under `features/`. Keep all local input and derived data untracked.
