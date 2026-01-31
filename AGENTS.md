# AGENTS.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a final year thesis research project on **Student Performance Prediction with Explainable AI & Fairness**. The project uses Machine Learning and Deep Learning (LSTM, Diffusion Models) to predict student academic performance, with emphasis on model explainability (SHAP, LIME) and fairness analysis.

The repository is organized into three main areas:
- **CodeBase/**: Production-ready code, final models, and thesis results
- **Literature/**: Research papers and individual contributor workspaces for experiments
- **Thesis_Paper/**: LaTeX manuscript files

## Repository Structure

### CodeBase (Main Production Code)
- `CodeBase/data/`: Primary datasets (student-mat.csv, student-por.csv from UCI)
- `CodeBase/src/`: Main prediction pipeline in Jupyter notebook
- `CodeBase/result/`: Model performance outputs and metrics
- `CodeBase/src/.spenv/`: Virtual environment (Python 3.10)

### Literature (Experimental Sandbox)
- `Literature/Papers/`: Shared research papers
- `Literature/Istiaq's-Workplace/`: LSTM models, XAI methods (SHAP, LIME, DICE, CEM), fairsynedu experiments
- `Literature/Nazme's-Workplace/`: Literature review drafts
- `Literature/Maria's-Workplace/`: Paper summaries

### Thesis Paper
- LaTeX source files and figures for academic publication

## Development Setup

### Initial Setup
```bash
cd CodeBase
python3 -m venv .spenv  # If virtual env doesn't exist
source .spenv/bin/activate  # On Linux/Mac
pip install -r requirements.txt
```

### Required Dependencies
- Python 3.10
- pandas (1.5.3)
- numpy (1.25.2)
- scikit-learn (1.2.2)
- xgboost (1.5.0)
- imbalanced-learn (0.10.1)
- aif360 (0.5.0)
- shap (0.41.0)
- lime (0.2.0.1)
- TensorFlow/Keras (for LSTM models in experimental workspace)

## Running the Main Pipeline

### Primary Notebook
The main prediction pipeline is in `CodeBase/src/student_performance_prediction.ipynb`:
```bash
cd CodeBase/src
source .spenv/bin/activate
jupyter notebook student_performance_prediction.ipynb
```

Alternatively, view in nbviewer: https://nbviewer.org/github/Istiaq-Alam/Student-Performance-Prediction-with-Explainable-AI/blob/main/CodeBase/src/student_performance_prediction.ipynb

### Notebook Pipeline Steps
The notebook executes the following workflow:
1. Data preprocessing and binary classification (pass: >=10, fail: <10)
2. Feature engineering and categorical encoding
3. Train-test split
4. SMOTE for class imbalance handling
5. Model training: Logistic Regression, Random Forest, XGBoost
6. Hyperparameter tuning (GridSearchCV/RandomizedSearchCV)
7. Model evaluation (accuracy, F1, precision, recall, ROC-AUC)
8. Fairness analysis with AIF360 (Reweighing, Demographic Parity, Equalized Odds)
9. Explainability: SHAP force plots, summary plots
10. Explainability: LIME explanations
11. Results saved to `CodeBase/result/model_performance.csv`

## Experimental Code Structure

### LSTM/Bi-LSTM Models
Located in `Literature/Istiaq's-Workplace/evaluating-explainers-experimental/scripts/`:
- `LSTM.py`: Bidirectional LSTM implementation for time-series student performance prediction
- Uses TensorFlow/Keras with sequential architecture: Masking → Bidirectional LSTM (64) → Bidirectional LSTM (32) → Dense (sigmoid)
- Trained with Adam optimizer, binary crossentropy loss
- Evaluation metrics: accuracy, balanced accuracy, precision, recall, F1, AUC

### XAI Methods (Experimental)
Separate Python scripts for explainability:
- `SHAP.py`: SHAP explainer implementations
- `LIME.py`: LIME explanations
- `DICE.py`: DiCE counterfactual explanations
- `CEM.py`: Contrastive Explanation Method
- `PDP.py`: Partial Dependence Plots
- `data_helper.py`: Data loading utilities

### Fairness Experiments
`Literature/Istiaq's-Workplace/fairsynedu-working-rn/`:
- Diffusion model experiments for fair synthetic educational data generation
- Uses AIF360 for bias detection and mitigation
- Configuration: `config_oulad.yaml`

## Key Datasets

Primary datasets (UCI Student Performance Dataset):
- `student-mat.csv`: Mathematics course student data
- `student-por.csv`: Portuguese course student data

Additional datasets in `CodeBase/data/`:
- `Student_Performance.csv`
- `Student_Performance_Dataset.csv`
- `StudentsPerformance.csv`

Source: Cortez and Silva, 2008 - https://archive.ics.uci.edu/ml/machine-learning-databases/00320/

## Working with Virtual Environments

Each workspace has its own `.spenv` virtual environment:
- Main: `CodeBase/src/.spenv/`
- Trial: `CodeBase/Trial/.spenv/`
- Fairsynedu: `Literature/Istiaq's-Workplace/fairsynedu-working-rn/.spenv/`

Always activate the appropriate environment before running code.

## Code Organization Principles

### Clean Room vs Sandbox
- **CodeBase**: Only finalized, working code. Direct changes should be tested and validated.
- **Literature**: Experimental sandbox for trying new approaches, individual work, and iterations.
- Move code from Literature → CodeBase only when finalized for thesis results.

### Multi-Contributor Workflow
- Istiaq: Model development, XAI implementation, LSTM experiments
- Nazme: Literature review, documentation
- Maria: Research analysis, paper summarization

When working across contributor workspaces, respect individual experimental setups and virtual environments.

## Model Architecture Notes

### Binary Classification Target
All models predict binary outcomes:
- Pass: G3 >= 10 (final grade)
- Fail: G3 < 10

### LSTM Input Shape
LSTM models expect reshaped temporal data:
- Input: `(n_weeks * n_features,)` flattened
- Reshaped to: `(n_weeks, n_features)` for LSTM processing
- Masking value: 1.0 (for padded sequences)

### Fairness Protected Attributes
Primary protected attribute for fairness analysis:
- `sex_M`: Gender (Male=1, Female=0)
- AIF360 Reweighing applied to balance bias

### Explainability Considerations
- SHAP: Use TreeExplainer for tree-based models (XGBoost, Random Forest)
- SHAP: Use KernelExplainer for black-box models
- LIME: Discretize continuous features appropriately for tabular data
- CEM: Requires TensorFlow 1.x compatibility mode (see LSTM.py lines 34-36)

## Important File Locations

- Main production code: `CodeBase/src/student_performance_prediction.ipynb`
- Results output: `CodeBase/result/model_performance.csv`
- Requirements: `CodeBase/requirements.txt`
- LaTeX thesis: `Thesis_Paper/Thesis_Template/` or `Thesis_Paper/Thesis_Template_with_external/`
- Research papers: `Literature/Papers/`

## Notes

- Python version requirement: 3.10 (system has 3.13, but virtual envs use 3.10)
- Virtual environments (`.spenv`) are gitignored
- Datasets are NOT gitignored (included in repo for reproducibility)
- LaTeX auxiliary files are gitignored (see .gitignore)
- No automated test suite currently exists
- No linting/formatting configuration files present
