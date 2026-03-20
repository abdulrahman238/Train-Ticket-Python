# Train-Ticket-Python
This project analyzes mock National Rail train ticket data in the UK from Jan–Apr 2024. The dataset includes ticket types, travel dates &amp; times, departure &amp; arrival stations, prices, and journey status.
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
```
df = pd.read_csv("railway.csv")
```
# Fill missing values
```
df["Railcard"] = df["Railcard"].fillna("Unknown")
df["Reason for Delay"] = df["Reason for Delay"].fillna("Unknown")
```
# Convert to datetime
```
df["Date of Journey"] = pd.to_datetime(df["Date of Journey"], errors="coerce")
df["Date of Purchase"] = pd.to_datetime(df["Date of Purchase"], errors="coerce")
```
# Extract date parts
```
df["Month_Journey"] = df["Date of Journey"].dt.month_name()
df["Day_Journey"] = df["Date of Journey"].dt.day_name()
df["Year_Journey"] = df["Date of Journey"].dt.year
df["Month_Purchased"] = df["Date of Purchase"].dt.month_name()
df["Day_Purchased"] = df["Date of Purchase"].dt.day_name()
df["Year_Purchased"] = df["Date of Purchase"].dt.year
```
# KPIs
```
Total_Revenue = df["Price"].sum()
Total_Journey = len(df)
avg_price = round(df["Price"].mean(), 2)

print(f"Total Revenue: ${Total_Revenue:,}")
print(f"Total Journeys: {Total_Journey:,}")
print(f"Average Price: ${avg_price:,}")
```
# Visualizations
```
plt.figure(figsize=(6,4))
plt.text(0.05, 0.7, f"Total Revenue\n${Total_Revenue:,}", fontsize=16, weight='bold', color='green', ha='left')
plt.text(0.05, 0.45, f"Avg Price\n${avg_price:,}", fontsize=16, weight='bold', color='orange', ha='left')
plt.text(0.05, 0.2, f"Total Journey\n{Total_Journey:,}", fontsize=16, weight='bold', color='blue', ha='left')
plt.axis("off")
~
plt.show()
```

# 🐍 Python & Data Science Tools

- [![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/) **Python**
- [![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat&logo=jupyter&logoColor=white)](https://jupyter.org/) **Jupyter**
- [![Jupyter Notebook](https://img.shields.io/badge/Jupyter%20Notebook-F37626?style=flat&logo=jupyter&logoColor=white)](https://jupyter.org/) **Jupyter Notebook**
- [![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white)](https://numpy.org/) **NumPy**
- [![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white)](https://pandas.pydata.org/) **pandas**
