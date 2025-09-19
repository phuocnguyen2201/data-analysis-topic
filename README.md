## Salary Prediction – Football Player Data Analysis

This repository contains an exploratory data analysis and baseline salary prediction workflow for professional football (soccer) players using the dataset in `SalaryPrediction.csv` and the analysis notebook `Group_Project.ipynb`.

### What this project does
- **Explores** the dataset: distributions, outliers, correlations, and league/club/position breakdowns
- **Cleans**/preprocesses the data: fixes types (e.g., currency strings), handles missing values, and normalizes categorical fields
- **Builds baselines** for salary prediction with simple, transparent models
- **Evaluates** models with appropriate regression metrics and sanity checks

### Files in this repo
- `Group_Project.ipynb`: Main Jupyter Notebook with the full analysis and modeling workflow
- `SalaryPrediction.csv`: Source dataset of player attributes and wages

### Dataset overview
The CSV includes the following columns (inferred from the header):
- `Wage` (target): Player wage/salary (currency-formatted string, includes commas/quotes)
- `Age`: Player age (integer)
- `Club`: Current club
- `League`: League name (e.g., Premier League, La Liga)
- `Nation`: National team (ISO-like short code or country code)
- `Position`: Field position (e.g., Forward, Midfielder, Defender, Goalkeeper)
- `Apps`: Club appearances (career or season as provided)
- `Caps`: National team appearances

Notes observed from a quick glance:
- `Wage` is stored as a string with commas/quotes and must be converted to numeric
- Some categorical spellings may vary (e.g., Midfilder vs Midfielder); consider normalization
- Club/league/nation naming can include spaces and special characters and may require careful parsing

### Getting started
1) Install Python (3.9+ recommended)
2) Create and activate a virtual environment (Windows PowerShell):
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```
3) Install dependencies:
```powershell
pip install --upgrade pip
pip install jupyter pandas numpy matplotlib seaborn scikit-learn
```
4) Launch Jupyter and open the notebook:
```powershell
jupyter notebook
```
Open `Group_Project.ipynb` and run cells top-to-bottom.

### Typical workflow in the notebook
- Load the CSV and inspect schema, head, and summary stats
- Clean and engineer features:
  - Parse `Wage` to numeric (remove commas/quotes)
  - Normalize text fields (e.g., `Position`, `League`), fix typos, and standardize case
  - One-hot encode categorical variables
  - Scale/standardize numerical features if required by the model
- Split the data (train/validation/test) with reproducible random state
- Fit baseline regressors (e.g., Linear Regression, Random Forest Regressor)
- Evaluate with RMSE/MAE/R2 on validation/test sets
- Interpret results: feature importances, partial dependence (if applicable)

### Reproducibility tips
- Set a fixed `random_state` for splits and model initialization
- Record exact package versions (`pip freeze > requirements.txt`) once your environment is stable
- If the dataset changes upstream, re-run the notebook end-to-end and compare metrics

### Potential extensions
- Add more robust text normalization for `Club`, `League`, `Position`
- Create domain features (e.g., per-90 stats if available, league strength indices)
- Hyperparameter tuning with `GridSearchCV`/`RandomizedSearchCV`
- Model comparison (e.g., XGBoost/LightGBM/CatBoost)
- Cross-validation and learning curves
- Simple API or streamlit dashboard for predictions

### Known caveats
- Currency formatting in `Wage` must be cleaned before modeling
- Inconsistent labels (e.g., typos) can degrade model performance if not normalized
- Dataset may include outliers; consider winsorizing or robust models

### Acknowledgements
- Public football data sources and club/league naming conventions
- Open-source Python ecosystem (Jupyter, pandas, numpy, matplotlib, seaborn, scikit-learn)
