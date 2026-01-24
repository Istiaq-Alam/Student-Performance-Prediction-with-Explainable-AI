# Student Performance Prediction with Explainable AI & Fairness

Welcome to the central repository for our final year thesis research. This project focuses on predicting student academic performance using Machine Learning and Deep Learning (LSTM, Diffusion Models), while emphasizing model explainability (SHAP, LIME) and fairness.

## 📂 Repository Navigation

Select a directory below to navigate to the specific workspace:

| Directory | Description | Status |
| :--- | :--- | :--- |
| [**💻 CodeBase**](./CodeBase) | **The Main Project.** Contains the cleaned, production-ready code, datasets, and final models used for the thesis results. | 🟢 Active |
| [**📚 Literature & Sandbox**](./Literature) | **Research Hub.** Contains literature reviews, PDF papers, and **individual contributor workspaces** (Istiaq, Maria, Nazme) for experiments. | 🟡 Ongoing |
| [**Thesis Paper**](./Thesis_Paper) | **The Manuscript.** Contains the LaTeX files, images, and bibliography for the final research paper. | 🔴 Draft |

---

## 🚀 Getting Started (Main Codebase)

To run the main project code, please follow these steps:

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
   ```
2. **Navigate to the CodeBase:**
   ```bash
   cd CodeBase
   ```
3. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
4. **Run the Analysis:**
   - Open `src/student_performance_prediction.ipynb` to view the primary prediction pipeline.
   - Check `result/` for generated performance metrics.

--- 

## 🏗️ Project Structure Overview
1. `CodeBase`
This is the "Clean Room." Only finalized code goes here.
- `data/`: Raw datasets (student-mat.csv, student-por.csv).
- `src/`: Source code, notebooks, and main scripts.
- `result/`: Model performance CSVs and outputs.

2. `Literature` (Collaborator Workspaces)
This is the "Sandbox."
- `Papers/`: Shared collection of research papers we are studying (e.g., Evaluating the Explainers, Fairness in Student Prediction).
- Individual Workspaces:
  - 👤 [Istiaq](https://github.com/Istiaq-Alam): Working on LSTM models, XAI methods (SHAP, LIME, DICE), and `fairsynedu`.
  - 👤 [Nazme](https://github.com/Nazme10): Literature review and initial drafts.
  - 👤 [Maria](https://github.com/mariafardus): Summaries of academic performance prediction papers.

3. `Thesis_Paper`
Contains the academic output.
- LaTeX source files.
- High-resolution figures generated from the CodeBase.

---

## 🛠️ Key Technologies & Methods
- Models: LSTM, Bi-LSTM, Diffusion Models.
- Explainability (XAI): SHAP, LIME, DICE, CEM (Counterfactual Explanations).
- Fairness: Bias detection in educational data (fairsynedu).
- Data: Student Performance Data Set (Cortez and Silva, 2008).

---

## 🤝 Contributors
- [Istiaq](https://github.com/Istiaq-Alam) - Model Development & XAI Implementation
- [Nazme](https://github.com/Nazme10) - Literature Review & Documentation
- [Maria](https://github.com/mariafardus) - Research Analysis & Summarization

---

## 📝 License
This project is for academic research purposes.
