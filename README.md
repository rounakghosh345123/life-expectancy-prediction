# Global Life Expectancy Prediction

Predicting a country's life expectancy from real health, economic, and education indicators — sourced directly from the World Bank, not a pre-cleaned Kaggle CSV. Identifies which factors most influence health outcomes, relevant to global health policy prioritization.

## Problem Statement

*(Fill in once you've run the notebook)*

Example starting point:
> Understanding which development factors most influence life expectancy helps policymakers and health organizations prioritize limited resources. This project builds a predictive model on real World Bank development data to quantify those relationships and identify countries whose outcomes diverge from what their indicators would predict.

## Dataset

- **Source:** [World Bank World Development Indicators](https://databank.worldbank.org/source/world-development-indicators) — official institutional data, queried and exported directly, not a Kaggle mirror
- **Indicators used:** Life expectancy, GDP per capita, health expenditure, primary school enrollment, measles immunization rate, under-5 mortality, HIV prevalence, population
- **Format:** Multi-country, multi-year panel data, self-assembled via World Bank's DataBank query tool

## Approach

1. **Data Acquisition** — queried 8 real indicators across all countries and multiple years directly from World Bank DataBank, exported as CSV
2. **Reshaping** — converted from the World Bank's wide year-column export format into a clean, model-ready country-year row structure (a genuine real-world data engineering step, not something a typical Kaggle CSV requires)
3. **Cleaning** — handled World Bank's `'..'` missing-value convention, imputed missing indicators using year-specific medians (not a single global median, to account for reporting quality changing over time)
4. **EDA** — examined relationships between each indicator and life expectancy
5. **Feature Engineering** — log-transformed GDP per capita and Population to correct heavy skew
6. **Modeling** — compared Linear Regression, Random Forest, and XGBoost; tuned the best model with GridSearchCV
7. **Explainability** — feature importance analysis showing which indicators drive predictions most
8. **Policy Framing** — identified countries whose actual life expectancy diverges most from what their indicators predict, flagging cases worth deeper investigation

## Key Results

*(Fill in with your actual numbers)*

| Model | R² | MAE (years) | RMSE (years) |
|---|---|---|---|
| Linear Regression | 0.XX | X.X | X.X |
| Random Forest | 0.XX | X.X | X.X |
| XGBoost (tuned) | **0.XX** | **X.X** | **X.X** |

**Top predictive features:**
1. *(e.g. Under-5 Mortality — strongest predictor)*
2. *(e.g. HIV Prevalence — ...)*
3. *(e.g. GDP per Capita — ...)*

## Business/Policy Impact

*(Paste your Phase 7 takeaway)*

> Countries over-performing their indicator-predicted life expectancy may have effective health interventions not captured in these 7 features — worth case-study attention. Countries under-performing may warrant investigation into gaps between resource levels and actual outcomes.

## How to Run

```bash
git clone <your-repo-url>
cd life-expectancy-prediction

conda create -n lifeexp python=3.10 -y
conda activate lifeexp
pip install -r requirements.txt

jupyter notebook life_expectancy_project.ipynb
streamlit run app.py
```

**Note:** the raw dataset isn't included in this repo (World Bank data is large and freely re-downloadable) — follow the data acquisition steps at the top of the notebook to generate `worldbank_data.csv` yourself before running.

## Live Demo

*(Add your Streamlit Community Cloud link once deployed)*

🔗 [Try the app here](#)

## Screenshots

*(Add: correlation heatmap, feature importance chart, predicted-vs-actual scatter plot, and the app in action)*

## Tech Stack

Python · pandas · scikit-learn · XGBoost · World Bank Open Data · Streamlit
