# MMM Weekly – Revenue Modeling

This project builds a **Marketing Mix Model (MMM)** using weekly data to explain and forecast **Revenue** based on marketing activities and business drivers.  
The analysis uses **ElasticNet regression** with Bayesian hyperparameter tuning, proper time-series validation, and a causal perspective where **Google spend is treated as a mediator** between social/display and revenue.

---

## 📂 Repository Structure
mmm-weekly/
├── data/
│   └── Assessment2_MMM_Weekly.csv   # weekly dataset
├── mmm-analysis2.ipynb               # full Colab-ready notebook
├── Short_Writeup.md                  # short project summary
└── README.md                         # this file


---

## 📊 Dataset

The dataset (`Assessment2_MMM_Weekly.csv`) contains weekly observations of:

- **Target variable**
  - `revenue` – weekly revenue

- **Media spend channels**
  - `facebook_spend`
  - `google_spend`
  - `tiktok_spend`
  - `instagram_spend`
  - `snapchat_spend`

- **Business drivers**
  - `average_price`
  - `promotions`
  - `emails_send`
  - `sms_send`
  - `social_followers`

This structure supports modeling both **product levers** (price, promotions) and **media levers** (digital spends).

---

## ⚙️ How to Run

1. Clone this repository or download the files.  
2. Open `notebook.ipynb` in **Google Colab** or Jupyter.  
3. Install dependencies if needed:
   ```python
   !pip install optuna scikit-learn pandas matplotlib seaborn statsmodels
