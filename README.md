# Tucson Crime Analysis: Income and Street Lighting

A multivariate analysis of Tucson Police crime and arrest data against
neighborhood income and city streetlight locations, testing two hypotheses:

1. **Crime and income.** Do thefts and violent crimes occur more often in richer
   or poorer neighborhoods?
2. **Crime and streetlights.** Does the presence of city streetlights influence
   crime rates, particularly at night?

Final project for CSc 380 at the University of Arizona, spring 2025.

The full 21-page write-up with figures, methodology, and citations is
[`report/final.pdf`](report/final.pdf). Start there.

## What's here

- `final_report_notebook_code.py`: the analysis, exported from the Colab
  notebook it was developed in. Loading, cleaning, EDA, and modeling.
- `datasets/`: all four source CSVs, checked in so the analysis is reproducible.
- `report/`: the LaTeX source, figures, and compiled PDF.

## Data

All four datasets are public, from the City of Tucson open data portal.

| Dataset | Source |
|---|---|
| Tucson Police reported crimes | [gisdata.tucsonaz.gov](https://gisdata.tucsonaz.gov/) |
| Tucson Police arrests, 2021 | [gisdata.tucsonaz.gov](https://gisdata.tucsonaz.gov/datasets/7c7c881c1fff44ec8a8c2ab612700271_67/explore) |
| City of Tucson streetlight locations | [gisdata.tucsonaz.gov](https://gisdata.tucsonaz.gov/datasets/09ed59b6aae2483aa1bd32837d4aa7e5_19/explore) |
| Neighborhood income | [gisdata.tucsonaz.gov](https://gisdata.tucsonaz.gov/datasets/59f033d07eae41b0bdc21db87375d721_0/explore) |

## Running it

The script was written in Colab and reads from
`/content/drive/MyDrive/datasets/`. To run it locally, point those paths at this
repo's `datasets/` directory.

```bash
pip install pandas numpy matplotlib seaborn geopandas shapely geopy \
            scikit-learn imbalanced-learn statsmodels
python final_report_notebook_code.py
```

## Methods

- Ridge regression on hourly crime counts by police division.
- Random Forest and logistic regression to classify high-crime wards from income
  and streetlight features.
- OLS to estimate how income and streetlight count relate to crime counts.

## Findings

**Hypothesis 1 held.** Median household income is inversely associated with
crime counts. The correlation between median household income and crime count is
-0.32, and the relationship is significant in OLS (Model 1, R2 = 0.101). Wards 3
and 5, the lowest-income wards, carry the highest rates of both larceny and
violent crime.

**Hypothesis 2 did not hold.** Streetlight count is *positively* associated with
crime, not negatively. OLS Model 2 (R2 = 0.461) and Random Forest feature
importance (0.55 for streetlight count) both point the same direction, and the
correlation between streetlight count and the nighttime share of crime is only
0.20. The most likely reading is that lighting gets installed in response to
crime rather than preventing it. This runs against Welsh and Farrington's
finding that improved lighting reduces some crime types.

Crime and arrest counts correlate at 0.97, which says policing tracks reported
crime closely but also raises a question about over-policing in lower-income
wards that this data cannot settle.

Random Forest classified high-crime wards more accurately than logistic
regression (0.97 versus 0.75), though with only six wards that number describes
this dataset rather than generalizing.

### Limits

This is observational data, so every relationship above is an association and
none of it establishes cause. Crime counts measure *reported* crime, which
carries reporting and enforcement bias. The streetlight data is a location
inventory with no maintenance or outage history, so a mapped light is not
necessarily a lit one.

## License

MIT. See [LICENSE](LICENSE).
