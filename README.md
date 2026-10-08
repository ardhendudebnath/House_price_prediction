# House_price_prediction

𝙋𝙧𝙚𝙙𝙞𝙘𝙩𝙞𝙣𝙜 𝙃𝙤𝙪𝙨𝙚 𝙋𝙧𝙞𝙘𝙚𝙨 𝙬𝙞𝙩𝙝 𝙈𝙖𝙘𝙝𝙞𝙣𝙚 𝙇𝙚𝙖𝙧𝙣𝙞𝙣𝙜


This repository contains a machine learning model that predicts house prices based on various features such as location, number of bedrooms, square footage, and more. The model is trained on a dataset of historical house sales and uses a combination of regression algorithms to make accurate predictions.

𝙁𝙚𝙖𝙩𝙪𝙧𝙚𝙨:


Data Preprocessing: Handling missing values, feature scaling, and encoding categorical variables
Model Training: Implementing and comparing different regression algorithms (e.g. Linear Regression, Decision Trees, Random Forest)
Model Evaluation: Measuring performance metrics (e.g. Mean Absolute Error, Mean Squared Error, R-Squared)
Deployment: Creating a user-friendly interface for users to input features and receive predicted house prices

𝙏𝙚𝙘𝙝𝙣𝙤𝙡𝙤𝙜𝙞𝙚𝙨 𝙐𝙨𝙚𝙙:

Python,
 Scikit-learn
, Pandas
, NumPy
, Matplotlib
, Seaborn

𝙂𝙤𝙖𝙡𝙨:


To develop a accurate and reliable house price prediction model
To provide a user-friendly interface for users to input features and receive predicted house prices
To continuously improve the model by incorporating new data and features

𝘾𝙤𝙣𝙩𝙧𝙞𝙗𝙪𝙩𝙞𝙤𝙣𝙨:

Bug fixes and improvements to the model and interface
Adding new features and datasets to improve model accuracy
Improving the user interface and user experience


---

## Results

Measured on `data.csv` — 4,600 rows. 49 rows priced at exactly $0 and the top
1% (above $2,016,000) are dropped, leaving 4,505. Ordinary least squares on log
price via `np.linalg.lstsq`, 80/20 split, errors reported in dollars on the
held-out 20%.

| Model | Features | RMSE | MAE | R² | Median error |
|---|---|---|---|---|---|
| cleaned + log target | 12 | $215,647 | $146,836 | 0.4263 | 22.4% |
| + log areas, age | 12 | $199,184 | $142,765 | 0.5105 | 23.2% |
| **+ city** | **55** | **$153,672** | **$96,253** | **0.7086** | **13.2%** |

**Location was the missing feature.** Adding 44 city indicators took R² from
0.43 to 0.71 and cut the median error from 22% to 13%. Every structural feature
in the original list — bedrooms, bathrooms, floor area, condition — is worth
less than knowing which city the house is in.

### Note on an earlier version

An earlier version fit on raw prices with no cleaning and reported
`Mean Squared Error: 991070536292` — an RMSE near **$995,000**, larger than most
of the houses in the data. That error was describing a single $26.6M sale, not
the model.

Cleaning fixed the metric; it did not fix the model. R² stayed near 0.43 until
location went in. The two are not the same thing, and it is worth being clear
about which one a change actually bought.

Implemented in numpy only, no pandas and no scikit-learn.
