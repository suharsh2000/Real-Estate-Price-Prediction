#  Bangalore House Price Prediction

This project predicts real estate prices in Bangalore based on key features like square footage, number of bedrooms (BHK), bathrooms, and location. It uses data cleaning, feature engineering, outlier removal, and regression models to estimate prices accurately.

##  Dataset

- **Source:** [Kaggle - Bengaluru House Price Data](https://www.kaggle.com/datasets/amitabhajoy/bengaluru-house-price-data)
- **Records:** ~13,000
- **Features Used:**
  - `location`
  - `size` (e.g., "2 BHK", "4 Bedroom")
  - `total_sqft`
  - `bath`
  - `price`

##  Data Cleaning

- Dropped unused columns: `society`, `availability`, `balcony`, etc.
- Converted `size` into numeric `bhk` values.
- Transformed `total_sqft` values from ranges to mean.
- Removed data:
  - Where total_sqft/BHK < 300
  - Where BHK price per sqft is abnormally lower than smaller BHKs
  - Where bathrooms > BHK + 2

## Feature Engineering

- Added `price_per_sqft`
- Grouped low-frequency locations as `"other"`
- One-hot encoded location column

##  Model Training

- **Features:** `total_sqft`, `bath`, `bhk`, and encoded `location`
- **Target:** `price` (in lakhs)
- **Train/Test Split:** 80/20
- **Algorithms Tested:**
  - Linear Regression  (Best performing)
  - Lasso Regression
  - Decision Tree Regressor
- **Tuning:** Performed using `GridSearchCV`

###  Best Model

```bash
Model: Linear Regression
Best Cross-Validation Score: ~0.818
