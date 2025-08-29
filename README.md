# Chicken Disease Classification Project

A complete machine learning pipeline for classifying diseases in chickens using computer vision and deep learning. This project is built with modular structure, version control using DVC (Data Version Control), and supports reproducible training and deployment.
---
## Project Overview

This repository enables an end-to-end training and serving pipeline to classify images of chickens for disease detection. It leverages:

- **DVC** for managing datasets, artifacts, and pipeline reproducibility.  
- **Config-driven architecture** — customizable via `config.yaml`, `params.yaml`, etc.  
- **CNN classifier module** — handles training, evaluation, and model saving in `src/cnnClassifier`.  
- **App Deployment** — with scripts like `app.py`, `main.py`, and templating via `template.py`.

---

## Repository Structure

Chicken-Disease-classification--Project/
├── .dvc/ # DVC metadata for data versioning
├── .github/workflows/ # CI/CD workflows
├── config/ # Configuration files (e.g., config.yaml, params.yaml)
├── research/ # Experiment logs, notebooks, or analysis
├── src/cnnClassifier/ # CNN model code, training and evaluation logic
├── templates/ # UI templates for web interface
├── app.py # App script for serving predictions
├── main.py # Entry point for pipeline orchestrations
├── template.py # Template utility for reporting or UI
├── dvc.yaml # DVC pipeline specification
├── dvc.lock # DVC lock file
├── params.yaml # Hyperparameters and experiment settings
├── requirements.txt # Python dependencies
├── setup.py # Package or install helper
├── dockerfile # Container configuration
├── scores.json # Evaluation metrics summary
├── README.md # Project documentation (you’re about to enhance it)
└── LICENSE (MIT) # Open-source licensing


---

## Getting Started

### Prerequisites

- Python 3.x  
- DVC installed (`pip install dvc`)  
- (Optional) Docker, if you want containerized execution

### Installation

cmd
git clone https://github.com/Rohitcodermanit/Chicken-Disease-classification--Project.git
cd Chicken-Disease-classification--Project
python3 -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt

Usage

Configuring the Run
Edit config/config.yaml and params.yaml to customize dataset paths, model parameters, and training options.
If using sensitive info (e.g., credentials), update secrets.yaml (optional).
Running the DVC Pipeline
dvc repro
This will execute the defined pipeline stages (data prep, training, evaluation) and produce artifacts such as trained models and metrics.

Model Serving

To launch the prediction interface:
python app.py
Then open http://localhost:5000 (or other specified port) to classify chicken images via the web UI.

How It Works

DVC Pipeline: Defined in dvc.yaml, orchestrates stages such as data ingest, preprocessing, model training, and evaluation.
CNN Classifier: Located within src/cnnClassifier, this module builds, trains, and saves a CNN-based model for disease prediction.
Configuration Management: Settings for experiments are externalized in YAML files, promoting reproducibility and easy experimentation.
Serving & UI: app.py uses templating (via templates/ and template.py) to offer a user-friendly interface for predictions.
Packaging & Deployment: The Dockerfile and .github/workflows (if configured) support automation and containerized deployment.

Evaluation Metrics

Model performance is logged in scores.json during pipeline execution. Metrics typically include:
Accuracy
Precision & Recall
F1-Score
Any other specified in your evaluation scripts

Contributing

Improvements and feature additions are welcome! You can enhance by:
Adding additional disease classes or datasets
Defining more evaluation metrics (e.g., ROC-AUC)
Adding unit tests or CI workflows
Containerizing the application further or adding GPU support

Suggested workflow:

git checkout -b feature/YourFeature
# Implement changes
git commit -m "Add feature description"
git push origin feature/YourFeature
