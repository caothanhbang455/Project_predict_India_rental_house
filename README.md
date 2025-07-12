# Indian Rental House Price Prediction

This project is a complete application of data preprocessing, analysis, and linear regression modeling to predict **house rental prices in India**, focusing on properties in **Delhi**.

> **Author**: Cao Thanh Bằng  
---

## Project Objective

The objective is to build a **Linear Regression model** that accurately predicts rental house prices using various property features (e.g., size, type, location, city, etc.). This involves a full data science pipeline — from cleaning and exploration to model building and evaluation.

---

## Dataset Description

- **Filename**: `Indian_housing_Delhi_data.csv`
- **Source**: Provided by instructor
- **Size**: ~5,000 records

### Feature Dictionary

| Feature                | Description                                              |
|------------------------|----------------------------------------------------------|
| House Type             | Type of house (e.g. apartment, villa, duplex)            |
| House Size             | Area in sq ft or sq meters                               |
| Location               | Neighborhood or area                                     |
| City                   | Always Delhi in this dataset                             |
| Latitude / Longitude   | Geolocation data                                         |
| Price (target)         | Rental price of the property                             |
| Currency               | Typically INR                                            |
| Number of Bathrooms    | Total bathrooms                                          |
| Number of Balconies    | Total balconies                                          |
| Negotiable             | Whether the price is negotiable (Yes/No)                |

---

## Key steps in analysis

### 1. Exploratory Data Analysis (EDA)
- Checked for **missing values**
- **Visualized distributions** of price, size, and number of rooms
- Created **correlation matrix** and **pairplots** to explore relationships
- Identified skewness and outliers in price

### 2. Data Cleaning & Preprocessing
- Handled missing data and incorrect types
- Encoded categorical features (e.g., `Negotiable`, `House Type`)
- Applied **log transformation** to `Price` for normalization

### 3. Feature Engineering
- Created `Price per Square Foot` metric
- Removed redundant columns
- Scaled numerical features for modeling

### 4. Linear Regression Model
- Train/Test split (80/20)
- Applied **Linear Regression** using `scikit-learn`
- Visualized predictions vs. actual prices
- Evaluated with:
  - `R² Score`
  - `MAE`, `RMSE`

---

## Results & Evaluation

|Remove outlier|Apply Scaler|R2 train|rmse train|R2 test|rmse test|
|---|---|---|---|---|---|
|Yes|Yes|0.847|67644.665|0.871|60481.347|
|No|Yes|0.892|88197.155|0.917|78568.548|
|Yes|No|0.877|59341.692|0.787|82916.955|
|No|No|0.897|86069.128|0.904|85241.854|

---

## Conclusion

- The best result is the model at case 1.1 (model11) with high R^2 in both 
train and test set, but rmse in train test is highest in 4 cases.

- although remove outlier have small rmse, it lower in R square in both 
train and test (case model10 and model20)

- applying scaler is not impacted too much, if we consider model10 and model 20
the R2 is reduced nearly 10% (this is also depend on test/train when splitting).
This is also the case for model11 and model22, just
reducing to 0.1%
---

## Running

```bash
# Clone this repository
git clone https://github.com/caothanhbang455/Project_predict_India_rental_house.git

# Open the notebook
jupyter notebook FullName_CK_K304_HV.ipynb

# Create virtual environment with Python 3.9
python3.9 -m venv venv

# Activate (Linux/macOS)
source venv/bin/activate

# Activate (Windows)
venv\Scripts\activate

# install libraries
pip install --upgrade pip

# Install core packages
pip install pandas numpy matplotlib seaborn scikit-learn

# Install additional custom packages
pip install ttth-mds5-analyzer
pip install preprocess
