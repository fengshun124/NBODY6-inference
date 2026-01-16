# NBODY6 Inference Workspace

This repository provides tools to transform raw [`NBODY6`](https://github.com/nbodyx/Nbody6) simulation outputs into analysis-ready datasets and train machine learning models to infer star cluster properties from observable stellar features. The simulation data is sourced from [*Dinnbier et al.* (2022)](https://ui.adsabs.harvard.edu/abs/2022A&A...659A.169D). This project was developed as part of my Master's thesis at the University of Liverpool.

The NBODY6 simulation data used with this code are NOT distributed in this repository. I DO NOT have the rights to redistribute the proprietary simulation data. If you wish to obtain the data for research purposes, please contact the original authors directly.

## Repository Structure

- [`data-pipeline/`](./data-pipeline/): Contains scripts for processing NBODY6 simulation outputs, extracting relevant statistics, and preparing datasets for analysis. See the [data-pipeline README](./data-pipeline/README.md) for detailed instructions.

- [`machine-learning/`](./machine-learning/): Includes code for preparing data, training machine learning models, and evaluating their performance in inferring star cluster properties based on per-stellar features. See the [machine-learning README](./machine-learning/README.md) for detailed instructions.

## Requirements

Python 3.12+ with the following packages (see [`requirements.txt`](./requirements.txt) for pinned versions, or [`data-pipeline/requirements.txt`](./data-pipeline/requirements.txt) and [`machine-learning/requirements.txt`](./machine-learning/requirements.txt) for subdirectory-specific dependencies):

- `click`
- `joblib`
- `numpy`
- `pandas`
- `python-dotenv`
- `pytorch_lightning`
- `scikit-learn`
- `torch`
- `torchmetrics`
- `tqdm`
- `h5py`
- `pot`
- `astropy`
- `pyarrow`