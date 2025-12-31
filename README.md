`IMDB Reviews Sentiment Analysis`

Overview
--------
This repository contains an end-to-end sentiment analysis project built around IMDB movie reviews. It includes data ingestion and preprocessing, feature engineering, model training and evaluation, a simple Flask-based inference service.

Important Info
- First set your `MLFLOW_TRACKING_URI` and `REPO_OWNER` from remote dagshub repository.
  
Key Features
- **End-to-end pipeline:** Data ingestion, preprocessing, feature engineering, training, evaluation, and inference.
- **Modular codebase:** Core functionality is under the `src/` package for easy reuse and testing.
- **Deployment-ready inference:** A lightweight Flask app in `flask_app/` that serves predictions.
- **Experiment notebooks:** Notebooks & scripts under `notebooks/` to explore models and preprocessing.

Repository Structure
- **Source:** [src/](src)
	- [src/data/data_ingestion.py](src/data/data_ingestion.py) — data loading utilities
	- [src/data/data_preprocessing.py](src/data/data_preprocessing.py) — preprocessing steps
	- [src/features/feature_engineering.py](src/features/feature_engineering.py) — feature transforms
	- [src/model/train_model.py](src/model/train_model.py) — training entrypoint
	- [src/model/predict_model.py](src/model/predict_model.py) — prediction helpers
	- [src/model/register_model.py](src/model/register_model.py) — model registration utilities
- **Flask app:** [flask_app/](flask_app)
	- [flask_app/app.py](flask_app/app.py) — inference server
	- [flask_app/preprocessing_utility.py](flask_app/preprocessing_utility.py) — inference preprocessing
- **Notebooks:** [notebooks/](notebooks) — experiments and EDA
- **Models:** [models/](models) — saved model artifacts (gitignored)
- **Tests:** [tests/](tests) — unit tests for core functionality
- **Configs & metadata:** `params.yaml`, `dvc.yaml`, `setup.py`, and `requirements.txt`

Getting Started
---------------
Prerequisites
- Python 3.10+ and `pip`.
- (Optional) Create a virtual environment: `python -m venv .venv` and activate it.

Install dependencies
```powershell
pip install -r requirements.txt
```

Quick Usage
-----------
1. Prepare data: adjust paths in [src/data/data_ingestion.py](src/data/data_ingestion.py) or use the example CSV in `notebooks/data.csv` or get the full data from [kaggle](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews)
2. Preprocess & feature-engineer: First see the functionalities in `notebooks/` and then call functions in `src/data/` and `src/features/`.
3. Train a model:
```powershell
python -m src.model.train_model
```
1. Evaluate or run predictions locally using the provided scripts in `src/model/`.
2. Run the Flask inference server for deployment testing:
```powershell
cd flask_app
python app.py
```
Then open http://localhost:5000 and use the web UI, or POST JSON to `/predict`.

Tests
-----
Run the unit tests with:
```powershell
pytest -q
```

Contributing
------------
- Open issues or PRs for bug fixes and improvements.
- Follow the existing project structure and add tests for new functionality.

Troubleshooting
---------------
- If dependencies conflict, recreate a fresh virtual environment and reinstall from `requirements.txt`.
- Check `test_environment.py` for a quick environment sanity check.

License
-------
This project is released under the terms in the `LICENSE` file.

Contact
-------
For questions or help, open an issue in this repository.
