# Validation scope

Three notebooks pass schema validation; all code cells parse as Python. Outputs and execution counts are cleared. No dataset or feature tables are included. Each of the four model assets is byte-for-byte identical to its uploaded source, verified by SHA-256 after reading the model archive.

HDF5 configuration metadata were inspected, but TensorFlow models were not loaded or run. The two texture artifacts loaded in scikit-learn 1.8.0 with warnings identifying their saved version as 1.6.1. The manifest records sizes and hashes; the model guide records dimensions and feature order.

The notebooks have not been executed against the private study inputs. No accuracy claim or end-to-end reproducibility claim follows from these structural checks.
