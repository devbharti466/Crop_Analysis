# 🌾 Crop Yield and Production Exploratory Analysis (India APY Dataset)

An exploratory data analysis (EDA) notebook to inspect India’s agricultural APY data (Area–Production–Yield) by State, District, Crop, Year, and Season. Built in Python with Pandas and friends, it surfaces schema, missingness, suspicious zeros, distributions, and basic correlations to help you assess data quality before modeling or visualization.

***

## 🌟 Features

- ✅ Load APY.csv and display the first 10 sample rows
- ✅ Show all columns, dtypes, shape, and summary stats
- ✅ Reveal missing values and NaNs (e.g., in Crop and Production)
- ✅ Identify zero-inflation issues in Production and Yield
- ✅ Quick filtered views of problematic rows across States/Districts
- ✅ Numeric correlation matrix among Crop_Year, Area, and Yield
- ✅ Ready to extend with Matplotlib/Seaborn/Plotly visuals and GeoPandas maps

***

## 💻 Tech Stack

| Technology | Purpose |
|------------|---------|
| **Python** | Core language |
| **Pandas** | Data loading, wrangling, EDA |
| **NumPy** | Numeric utilities |
| **Seaborn** | Statistical plotting (ready for use) |
| **Matplotlib** | Base plotting (ready for use) |
| **Plotly Express** | Interactive charts (ready for use) |
| **GeoPandas** | Geospatial analysis (optional, ready for use) |

Note: The current notebook imports plotting/geospatial libraries but primarily runs data inspection steps. You can easily add charts and maps in new cells.

***

## 🗂️ Folder Structure

crop-apy-eda/  
- CropAnalysis.ipynb  
- APY.csv  # not included; place your dataset here or adjust path in notebook  
- README.md  
- requirements.txt  # optional, see below  

***

## 📦 Dataset Schema (Expected Columns)

- State (str): Indian state name  
- District (str): District within the state  
- Crop (str): Crop name  
- Crop_Year (int): Year of record (e.g., 1997–2020)  
- Season (str): Kharif, Rabi, Summer, Autumn, Whole Year, etc.  
- Area (float): Sown area (commonly hectares)  
- Production (float): Output amount (commonly tonnes)  
- Yield (float): Production per unit area (e.g., tonnes/ha)

Note: Ensure column names match these; adjust the notebook if your headers differ.

***

## 🔍 What the Notebook Does

1) Imports and Setup  
- Imports numpy, pandas, geopandas, matplotlib, plotly.express, seaborn.  
- Sets Pandas option to display all columns for easier inspection.

2) Load Data  
- Reads APY.csv using a Colab-style path:  
  - df = pd.read_csv("/content/APY.csv")  
- If running locally, change to df = pd.read_csv("APY.csv").

3) First Look  
- df.head(10) to view sample rows spanning multiple years and seasons.  
- Observed scale: ~345k rows × 8 columns in example runs.

4) Schema and Missingness  
- Displays dtypes: object for categoricals, int for year, float for metrics.  
- Surfaces missing values: NaNs appear notably in Crop and Production for some rows.  
- Shows boolean tables and filtered examples of NaNs/zeros.

5) Summary Statistics  
- Full numeric describe: ranges for Area/Yield, year span, medians/quantiles.  
- Highlights zero-inflation and potential outliers (e.g., Yield extremes).

6) Correlations  
- Computes correlation among numeric columns (Crop_Year, Area, Yield).  
- Example: weak relationships in the raw data; Production often excluded due to NaNs in that slice.

Why this matters  
- Establishes data quality baseline (missingness, zeros, ranges) before modeling.  
- Informs cleaning: unit checks, imputation strategies, and filtering rules.

***

## 🚀 How to Run Locally

1) Clone the repository:
```bash
git clone https://github.com/your-username/crop-apy-eda.git
cd crop-apy-eda
```

2) (Optional) Create and activate a virtual environment:
```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate
```

3) Install dependencies:
```bash
pip install pandas numpy seaborn matplotlib plotly geopandas
```

4) Add your dataset:
- Place APY.csv in the project root (same folder as the notebook), or update the path inside CropAnalysis.ipynb.

5) Launch Jupyter:
```bash
jupyter notebook
```
Open CropAnalysis.ipynb and run the cells in order.

***

## ☁️ Run in Google Colab

- Upload APY.csv to /content/ in your Colab runtime.  
- Open CropAnalysis.ipynb in Colab.  
- Ensure the path in the first cell is df = pd.read_csv("/content/APY.csv").  
- Run all cells.

***

## 🧹 Recommended Enhancements (Easy to Add)

- Data cleaning
  - Drop impossible rows (e.g., Area > 0 with Production  0 but Production = 0
  - Handle NaNs in Crop and Production (drop, impute, or mark)
  - Standardize units and check Yield = Production/Area consistency

- Visualizations
  - Distribution plots for Area/Production/Yield
  - Time-series trends by State/Crop/Season
  - Top crops by average Yield or Production
  - Outlier detection plots (boxplots, z-score filters)

- Geospatial
  - Join with district/state boundaries via GeoPandas
  - Choropleth maps of Yield/Production by year/season

- Modeling and Features
  - Rolling averages and seasonal indices
  - Encodings for Season/Crop/State
  - Basic forecasting/regression baselines

***

## 🧪 Troubleshooting

- FileNotFoundError: Verify APY.csv path. In Colab, keep it in /content or mount Drive and update the path.  
- Memory issues: Use read_csv with chunksize, or filter early by years/states/crops.  
- GeoPandas install errors: It may require system libraries; if you don’t need maps, you can skip installing geopandas.

***

## 📄 License

Add your preferred license (e.g., MIT). Ensure compliance with the original APY dataset’s licensing/attribution.

***

## 🙏 Acknowledgments

- APY (Area–Production–Yield) agricultural data for India  
- Open-source maintainers of Pandas, NumPy, Seaborn, Matplotlib, Plotly, and GeoPandas

***

## 📋 Example requirements.txt

If you prefer pinning:
```
pandas>=2.0
numpy>=1.24
seaborn>=0.12
matplotlib>=3.7
plotly>=5.15
geopandas>=0.14
```

***

## ✍️ Notes Observed from Current Notebook Output

- Years roughly 1997–2020; ~345k rows  
- NaNs: notably in Crop and Production for multiple rows  
- Many zeros in Production and Yield; may reflect true zero output or placeholders  
- Correlations among numeric columns are weak in raw form; stratify by crop/state/season and clean data for better insights

