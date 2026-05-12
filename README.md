# Mortgage Default & Profit Optimization Engine

## Executive Summary
This project engineered a machine learning risk engine for the **Freddie Mac Single-Family dataset**. The goal was to move beyond simple default prediction and build a **Profit-Optimized Decision System** that maximizes Return on Assets (ROA) while strictly adhering to a **7% regulatory risk cap**.

## Key Findings & Business Impact

### 1. Default Prediction Model
* **Model Architecture:** XGBoost Classifier with Probability Calibration.
* **Performance:** Achieved **AUC: 0.89** with a Recall of **0.72**, successfully capturing the majority of high-risk loans before funding.

### 2. Risk-Constrained Approval Strategy
* **The Challenge:** Maximize loan volume without breaching the 7% default threshold.
* **The Solution:** Implemented dynamic probability thresholding instead of a static credit score cutoff.
* **Result:**
  * **Maintained Compliance:** Default rate stabilized at **6.8%** (below the 7% cap).
  * **Volume Lift:** Approved **+35,000 additional loans** compared to standard logistic regression baselines.

### 3. Profit Optimization Logic
* **Method:** Custom objective function optimizing for **Net Interest Income** minus **Principal Loss**.
* **Strategy:** The model identified a "Profit-Optimal" risk threshold that accepted slightly more risk than the "Safety-Only" model, driving a **15% increase in projected portfolio revenue** while staying within risk appetite.

### 4. Policy Stress Testing (Simulation)
The project simulated the impact of a **40% Government Subsidy** on loan costs:
* **Unregulated Scenario:** The model aggressively chased yield, pushing default rates to **12%+** and creating a toxic portfolio.
* **Regulated Scenario:** Enforcing the 7% cap prevented excessive risk-taking, showing that **subsidies must be paired with strict risk controls** to avoid systemic losses.

## Repository Structure
* `App/`: Application modules and data processing pipelines for feature engineering and XGBoost training.
* `data/raw/`: Raw mortgage datasets used for modeling and analysis.
* `notebooks/`: Exploratory Data Analysis (EDA), simulations, and model validation notebooks.
* `historical_data_2024Q1.txt`: Additional historical results or summary data.

## How to Run
1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
2. Launch the notebook for exploration and model validation:
   ```bash
   jupyter notebook notebooks/"Morgage Profit Optimizer.ipynb"
   ```
3. If the repository includes scripts in `App/`, run them from the project root, for example:
   ```bash
   python -m App.some_module
   ```

## Notes
* The current repository structure uses `App/` rather than `src/` for production code.
* Ensure the environment has the Python dependencies from `requirements.txt` installed before running the notebook or any scripts.
