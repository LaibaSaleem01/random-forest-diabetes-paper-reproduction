# Diabetes Prediction with Random Forest  
## Reproduction of a Published 2025 Study

![Project banner](assets/project_banner.png)

This repository contains my independent reproduction of the experiments presented in the paper **“Efficient Diabetes Prediction Using Random Forests and Minimal Health Indicators on the BRFSS Dataset.”**

The project uses the balanced **BRFSS 2015 Diabetes Health Indicators dataset** to compare default, class-weighted, tuned, and feature-reduced Random Forest models.

> This repository is a research reproduction and learning project. It is not a clinical diagnostic system.

---

## Project Objective

The goal was to determine whether I could:

1. Reproduce the results reported in the published paper.
2. Examine the effect of Random Forest hyperparameter tuning.
3. Identify overfitting by comparing training and testing performance.
4. Measure how much performance is retained when the model uses fewer features.

---

## Dataset

The selected dataset contains:

- **70,692 records**
- **21 input features**
- **1 binary target variable**
- An approximately **50/50 class distribution**

Target classes:

- `0`: No diabetes
- `1`: Prediabetes or diabetes

The notebook downloads the dataset automatically through `kagglehub`, so the CSV file is not stored in this repository.

Dataset source:  
[BRFSS 2015 Diabetes Health Indicators Dataset on Kaggle](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset)

---

## Experiments

The following models were trained and evaluated:

- Default Random Forest
- Random Forest with `class_weight="balanced"`
- Tuned Random Forest using:
  - `n_estimators=200`
  - `max_depth=10`
  - `min_samples_split=10`
- Tuned Random Forest using the top:
  - 16 features
  - 12 features
  - 8 features
  - 4 features

The dataset was split into **80% training data and 20% testing data** using `random_state=42`.

---

## Main Results

| Model | Features | Train Accuracy | Test Accuracy | Precision | Recall | F1-score | Train–Test Gap |
|---|---:|---:|---:|---:|---:|---:|---:|
| Default Random Forest | 21 | 0.995102 | 0.737110 | 0.717210 | 0.780394 | 0.747469 | 0.257992 |
| Balanced Random Forest | 21 | 0.995102 | 0.738383 | 0.719298 | 0.779401 | 0.748145 | 0.256719 |
| Tuned Random Forest | 21 | 0.771100 | **0.752175** | **0.730584** | **0.796709** | **0.762215** | 0.018925 |
| Tuned RF — Top 16 | 16 | 0.772267 | 0.751609 | 0.730124 | 0.795999 | 0.761640 | 0.020658 |
| Tuned RF — Top 12 | 12 | 0.769880 | 0.748639 | 0.726448 | 0.795290 | 0.759312 | 0.021241 |
| Tuned RF — Top 8 | 8 | 0.765583 | 0.747083 | 0.725432 | 0.792737 | 0.757592 | 0.018500 |
| Tuned RF — Top 4 | 4 | 0.750889 | 0.740788 | 0.719912 | 0.785785 | 0.751407 | **0.010101** |

![Model performance comparison](assets/model_performance_comparison.png)

---

## Key Findings

### 1. The default model strongly overfit the training data

The default Random Forest achieved **99.51% training accuracy**, but only **73.71% testing accuracy**. The resulting gap of approximately **25.8 percentage points** indicated poor generalization.

### 2. Hyperparameter tuning greatly improved generalization

The tuned model reduced the training–test gap to approximately **1.89 percentage points** while increasing testing accuracy to **75.22%**.

![Generalization gap](assets/generalization_gap.png)

### 3. Class weighting provided little improvement

Using `class_weight="balanced"` produced only a very small improvement because the selected dataset was already approximately balanced.

### 4. Four features retained most of the predictive performance

The four most important features identified by the tuned model were:

1. **General Health**
2. **High Blood Pressure**
3. **Body Mass Index**
4. **Age**

The four-feature model achieved **74.08% accuracy** and an **F1-score of 75.14%**, remaining close to the full 21-feature model.

### 5. The reproduction closely matched the paper

The reproduced results were either identical or extremely close to the values reported by the authors, supporting the reproducibility of the main experiments.

---

## Repository Structure

```text
random-forest-diabetes-paper-reproduction/
│
├── assets/
│   ├── project_banner.png
│   ├── model_performance_comparison.png
│   └── generalization_gap.png
│
├── diabetes_prediction_random_forest.ipynb
├── Random_Forest_Paper_Reproduction_Report.pdf
├── requirements.txt
├── .gitignore
└── README.md
```

---

## How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/random-forest-diabetes-paper-reproduction.git
cd random-forest-diabetes-paper-reproduction
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

Activate it on macOS or Linux:

```bash
source .venv/bin/activate
```

### 3. Install the dependencies

```bash
pip install -r requirements.txt
```

### 4. Open the notebook

```bash
jupyter notebook diabetes_prediction_random_forest.ipynb
```

Run the notebook cells from top to bottom.

---

## Evaluation Metrics

The models were evaluated using:

- Training accuracy
- Testing accuracy
- Precision
- Recall
- F1-score
- Confusion matrix
- ROC curve and AUC
- Training–testing accuracy gap

Precision, recall, and F1-score were calculated for the positive class.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- KaggleHub
- Jupyter Notebook

---

## Original Paper

**Title:** Efficient Diabetes Prediction Using Random Forests and Minimal Health Indicators on the BRFSS Dataset  
**Authors:** Adnan Kutay Yüksel and Mehmet Serdar Güzel  
**Journal:** Journal of Artificial Intelligence and Human Sciences  
**Year:** 2025  
**Volume and issue:** 2(1)

The original article is cited for academic attribution. Its PDF is not redistributed in this repository.

---

## Limitations

- The BRFSS dataset is based on self-reported health information.
- The model should not be used as a medical diagnosis tool.
- The paper did not clearly state every random seed used in every experiment.
- Results may vary slightly across software versions or computing environments.

---

## Author

**Laiba Saleem**

This project was completed to gain practical experience with research reproduction, Random Forest tuning, feature importance, model evaluation, and overfitting analysis.
