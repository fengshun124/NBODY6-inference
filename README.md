# NBODY6 Inference Workspace

This repository transforms raw [`NBODY6`](https://github.com/nbodyx/Nbody6) simulation outputs into analysis-ready datasets and trains machine learning models to infer star cluster properties from observable stellar features. The simulation data source is [*Dinnbier et al.* (2022)](https://ui.adsabs.harvard.edu/abs/2022A&A...659A.169D). This project was developed as part of my Master's thesis at the University of Liverpool.

The NBODY6 simulation data used with this code are not distributed in this repository. I DO NOT have redistribution rights for these proprietary data. If you need the data for research, contact the original authors directly.

## Repository Structure

- [`data-pipeline/`](./data-pipeline/) contains scripts for processing NBODY6 outputs, extracting statistics, and preparing datasets. See the [data-pipeline README](./data-pipeline/README.md) for details.

- [`machine-learning/`](./machine-learning/) contains code for data preparation, model training, and evaluation. See the [machine-learning README](./machine-learning/README.md) for details.

## Requirements

Use Python 3.12+ with the packages below. Pinned versions are listed in [`requirements.txt`](./requirements.txt), [`data-pipeline/requirements.txt`](./data-pipeline/requirements.txt), and [`machine-learning/requirements.txt`](./machine-learning/requirements.txt).

- `astropy`
- `click`
- `joblib`
- `jupyter`
- `matplotlib`
- `numpy`
- `pandas`
- `pot`
- `pyarrow`
- `python-dotenv`
- `pytorch_lightning`
- `scikit-learn`
- `torch`
- `torchmetrics`
- `tqdm`

## Getting Started

- Clone the repository.

  ```bash
  git clone --recurse-submodules https://github.com/fengshun124/NBODY6-inference.git
  ```

- Install dependencies.

  ```bash
  cd ./NBODY6-inference
  pip install -r requirements.txt
  ```

Please refer to the respective READMEs in the [`data-pipeline/`](./data-pipeline/README.md) and [`machine-learning/`](./machine-learning/README.md) directories for detailed instructions on setting up the environment, preparing data, training models, and evaluating results.
