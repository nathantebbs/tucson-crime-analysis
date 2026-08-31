# Tucson crime analysis

I made this analysis as my final project for CSc 380 at the University of
Arizona in spring 2025. It compares Tucson Police crime and arrest records with
neighborhood income and city streetlight locations.

I asked two questions:

1. How do reported theft and violent crime counts vary with neighborhood income?
2. How do reported crime counts vary with the number of mapped streetlights?

The full 21-page report contains the figures, methods, citations, and model
output. Start with [`report/final.pdf`](report/final.pdf).

## Contents

- `final_report_notebook_code.py` contains the analysis exported from Colab.
- `datasets/` contains the four source CSV files.
- `report/` contains the LaTeX source, figures, and compiled report.

## Data

All four datasets came from the City of Tucson open data portal.

| Dataset | Source |
| --- | --- |
| Tucson Police reported crimes | [gisdata.tucsonaz.gov](https://gisdata.tucsonaz.gov/) |
| Tucson Police arrests from 2021 | [gisdata.tucsonaz.gov](https://gisdata.tucsonaz.gov/datasets/7c7c881c1fff44ec8a8c2ab612700271_67/explore) |
| City streetlight locations | [gisdata.tucsonaz.gov](https://gisdata.tucsonaz.gov/datasets/09ed59b6aae2483aa1bd32837d4aa7e5_19/explore) |
| Neighborhood income | [gisdata.tucsonaz.gov](https://gisdata.tucsonaz.gov/datasets/59f033d07eae41b0bdc21db87375d721_0/explore) |

## Running it

The script was written in Colab and reads from
`/content/drive/MyDrive/datasets/`. Point those paths at this repo's `datasets/`
directory before running it locally.

```sh
pip install pandas numpy matplotlib seaborn geopandas shapely geopy \
            scikit-learn imbalanced-learn statsmodels
python final_report_notebook_code.py
```

## Methods

- Ridge regression on hourly reported crime counts by police division
- Random Forest and logistic regression on ward income and streetlight features
- OLS estimates for income, streetlight count, and reported crime count

## Results

In this dataset, median household income and reported crime count have a
correlation of -0.32. Wards 3 and 5 have the lowest median incomes and the
highest reported larceny and violent crime counts. OLS Model 1 reports
R2 = 0.101.

Streetlight count has a positive association with reported crime count in OLS
Model 2. That model reports R2 = 0.461. Random Forest assigns streetlight count
a feature importance of 0.55. The correlation between streetlight count and the
nighttime share of reported crime is 0.20.

Those results do not show that streetlights cause crime or prevent it. The data
does not record when lights were installed, whether they worked, or why the city
placed them where it did.

Reported crime and arrest counts have a correlation of 0.97 in this dataset.
That number does not establish why the counts move together. It cannot separate
crime incidence, reporting, enforcement, or policing intensity.

Random Forest classified the six wards in this dataset with 0.97 accuracy. The
logistic regression result was 0.75. Six wards are not enough to treat either
number as evidence of performance on other cities or time periods.

## Limits

This is an observational analysis. Every result above is an association. Crime
counts cover reported crime and carry reporting and enforcement bias. The
streetlight data is a location inventory with no maintenance or outage history.

## License

MIT. See [LICENSE](LICENSE).
