# NBODY6 Inference Workspace

This workspace turns raw [`NBODY6`](https://github.com/nbodyx/Nbody6) simulation outputs into analysis-ready datasets and machine-learning experiments for star cluster property inference. The simulation data source is [*Dinnbier et al.* (2022)](https://ui.adsabs.harvard.edu/abs/2022A&A...659A.169D). This project was developed as part of my Master's thesis at the University of Liverpool.

The NBODY6 simulation data used with this code are not distributed in this repository. I DO NOT have redistribution rights for these proprietary data. If you need the data for research, contact the original authors directly.

The workspace is organised around two stages:

1. `data-pipeline/` parses raw NBODY6 outputs, assembles synchronized snapshots, and generates pseudo-observed catalogues plus summary statistics.
2. `machine-learning/` builds model-ready datasets from those pipeline outputs and trains inference models.

## Repository Structure

- [`data-pipeline/`](./data-pipeline/) processes NBODY6 outputs, extracts statistics, and prepares pseudo-observed datasets. See the [data-pipeline README](./data-pipeline/README.md) for details.
- [`machine-learning/`](./machine-learning/) builds training datasets, trains models, and evaluates inference performance. See the [machine-learning README](./machine-learning/README.md) for details.

## Requirements

Use Python 3.12+ for the workspace. Pinned versions are listed in [`requirements.txt`](./requirements.txt), [`data-pipeline/requirements.txt`](./data-pipeline/requirements.txt), and [`machine-learning/requirements.txt`](./machine-learning/requirements.txt).

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

## Typical Workflow

### Configure the Data Pipeline

Create `data-pipeline/.env` from `data-pipeline/.env.template`, then set:

- `SIM_ROOT_BASE`: path to the raw NBODY6 simulation outputs
- `OUTPUT_BASE`: destination for pipeline outputs
- `MPL_STYLE`: optional matplotlib style path

### Collect Simulation Statistics

Run the data-pipeline collection scripts from [`data-pipeline/`](./data-pipeline/):

```bash
cd ./data-pipeline
python ./src/collect_simulation_stats.py --slim
python ./src/collect_inclination_stats.py
```

The first script parses and assembles the raw NBODY6 files, caches `SnapshotSeries` outputs, and exports overall and annular statistics. The second computes inclination summaries for each snapshot. See the [data-pipeline README](./data-pipeline/README.md) for the full option set, including `--full` and `--log-file`.

### Inspect Pipeline Outputs

The pipeline writes results under `OUTPUT_BASE`, including:

- `cache/raw/` for cached intrinsic `SnapshotSeries`
- `cache/obs/` for cached pseudo-observed collections
- `stats/overall_stats/` for per-simulation overall statistics
- `stats/annular_stats/` for annular radial statistics
- `stats/inclination_stats/` for inclination summaries
- `log/` for batch and run-specific logs

### Train and Evaluate Models

After the pipeline outputs are prepared, continue with the workflow in [`machine-learning/`](./machine-learning/README.md) to build datasets, train models, and evaluate inference performance.

For module-specific setup and implementation details, continue with the READMEs in [`data-pipeline/`](./data-pipeline/README.md) and [`machine-learning/`](./machine-learning/README.md).
