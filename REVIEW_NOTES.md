# Review notes for the code release

This is a presentation and portability pass over the supplied notebooks, not a scientific correction of the experiments. Original cell indices below are zero-based and also appear in cell metadata. The source map records retained cells and input hashes.

## Items requiring author review

1. **Voting implementations differ.** In the main source, cell 20 uses majority-first selection; cell 30 uses a weighted helper with another texture weight. Both construct dictionaries keyed by the predicted label, so repeated labels overwrite previous weights rather than accumulate. Cell 24 uses a loop that accumulates weights. Confirm which implementation generated the paper results. Do not treat these as equivalent or silently substitute a corrected rule for published code.
2. **Fold summaries are not fold-wise retraining.** Main cell 24 divides fixed predictions with StratifiedKFold, but does not use the training indices to refit models. Describe that calculation accurately.
3. **A texture experiment scales before splitting.** Texture cell 58 fits StandardScaler on all samples. The later pipeline does not undo that information leakage. This historical block remains explicitly labelled; the earlier split-first experiment differs.
4. **Spot preprocessing and model filenames differ.** Training generators rescale by 1/255, while the single-image example passes raw pixels. The first export filename differs from the name loaded for inference. Confirm the intended preprocessing and checkpoint before reporting results.
5. **The release is incomplete for independent reproduction.** Curated images, labels, feature tables, the full original environment and disease-detector training code are absent. Four model artifacts are now supplied separately, with version metadata recorded in the model documentation. The public source dataset alone is insufficient to reproduce the exact study.

## Packaging changes

- Added titles, grouped sections, execution guidance, citation metadata and data-request information.
- Replaced hardcoded personal filesystem paths with a common configuration block.
- Removed embedded outputs, execution counts, attachments and original notebook metadata.
- Removed empty cells, comment-only legacy blocks, old narrative interpretations and ad hoc pip/unzip/Drive setup cells.
- Kept retained scientific code and its order; only path literals changed in those cells. Model choices, weights, seeds and evaluation logic were not corrected or rerun.

## Contact and licensing

The request address supplied by the author is `naoum1496@gmai.com`. Confirm the domain before publishing; this preparation has not silently changed it to gmail.com. A software reuse license has not been selected. Public visibility alone should not be described as an open-source license grant.
