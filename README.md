# Tucson Crime Analysis: Income and Street Lighting Impact

## Project Overview
This project analyzes the relationship between crime rates, neighborhood income levels, and streetlight presence in Tucson, Arizona. Using data from the Tucson Police Department, city streetlight locations, and neighborhood income statistics, the project tests two main hypotheses:
1. **Crime vs. Wealth**: Do thefts and violent crimes occur more frequently in richer or poorer neighborhoods?
2. **Crime vs. Streetlights**: Does the presence of streetlights influence crime rates, particularly at night?

The analysis employs data preprocessing, exploratory data analysis (EDA), and statistical modeling to uncover patterns and relationships. Models include Ridge Regression for hourly crime patterns, Random Forest and Logistic Regression for predicting high-crime wards, and Ordinary Least Squares (OLS) regression to assess the impact of income and streetlights on crime counts.

## Repository Structure
- **`csc_380_final_project.py`**: Main Python script containing data loading, preprocessing, EDA, and modeling code.
- **`datasets/`**: Directory for storing the datasets (not included in the repository; see [Data Sources](#data-sources) for download links).
- **`README.md`**: This file, providing an overview of the project and instructions for use.

## Data Sources
The project uses the following publicly available datasets:
- [Tucson Police Reported Crimes](https://drive.google.com/file/d/161iT39q-IjdAwfS4nYs8reUbW9VMtub1/view?usp=drive_link)
- [Tucson Police Arrests](https://drive.google.com/file/d/1bJnk0YaQ8xNQAeIJLMWA87VILOG2tEsl/view?usp=drive_link)
- [City of Tucson Streetlight Locations](https://drive.google.com/file/d/1PWVC5zM-AffD-WDhN-9h5rAeCRRMRtac/view?usp=drive_link)
- [Neighborhood Income](https://drive.google.com/file/d/1_Ys0zVHxuI-XVIq5UpbJJW0Y7Lf0_rPA/view?usp=drive_link)

**Note**: Download these datasets and place them in a `datasets/` folder in your Google Drive (`/content/drive/MyDrive/datasets/`) to run the code.

## Setup and Installation
This project was developed in Google Colab using Python 3. The following libraries are required:
- `pandas`, `numpy`: Data manipulation
- `matplotlib`, `seaborn`: Visualization
- `geopandas`, `shapely`, `geopy`: Geospatial analysis
- `scikit-learn`, `imblearn`: Machine learning
- `statsmodels`: Statistical modeling

### Installation Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/tucson-crime-analysis.git
   ```
2. Set up a Python environment (preferably in Google Colab or a local environment with Jupyter Notebook).
3. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn geopandas shapely geopy scikit-learn imblearn statsmodels
   ```
4. Mount your Google Drive in Colab and place the datasets in `/content/drive/MyDrive/datasets/`.
5. Run the `csc_380_final_project.py` script.

## Usage
1. Ensure the datasets are in the correct directory (`/content/drive/MyDrive/datasets/`).
2. Open `csc_380_final_project.py` in Google Colab or a Jupyter Notebook.
3. Run the script cell by cell to:
   - Load and preprocess the data
   - Perform exploratory data analysis (correlation matrices, scatter plots, etc.)
   - Train and evaluate Ridge Regression, Random Forest, Logistic Regression, and OLS models
   - Visualize results (e.g., regression surfaces, feature importance)

## Key Features
- **Data Preprocessing**: Cleans and integrates crime, arrest, streetlight, and income datasets, handling missing values and standardizing formats.
- **Exploratory Data Analysis**:
  - Correlation heatmaps to identify relationships between income, streetlights, and crime.
  - Scatter plots visualizing crime vs. income with streetlight density and night crime proportions.
  - Stacked bar charts showing crime types by ward and time period.
- **Modeling**:
  - **Ridge Regression**: Models hourly crime patterns by police division.
  - **Random Forest & Logistic Regression**: Predicts high-crime wards based on income and streetlight features.
  - **OLS Regression**: Analyzes the impact of income and streetlights on crime counts.
- **Visualizations**: Includes 3D regression surfaces, feature importance plots, and time-based crime distributions.

## Results
- **Hypothesis 1 (Crime vs. Wealth)**: A statistically significant inverse relationship was found between median household income and crime counts, with higher-income areas experiencing lower crime rates.
- **Hypothesis 2 (Crime vs. Streetlights)**: Streetlight presence has a stronger influence on crime counts than income, suggesting that increased lighting may reduce crime, particularly at night.
- **Model Performance**:
  - Random Forest and Logistic Regression models effectively predict high-crime wards, with feature importance highlighting streetlight count as a key predictor.
  - Ridge Regression reveals distinct hourly crime patterns across Tucson police divisions.

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit (`git commit -m "Add feature"`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a pull request.

Please ensure your code follows the existing style and includes appropriate comments.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Data provided by the City of Tucson and Tucson Police Department.
- Built with Python and open-source libraries including `pandas`, `scikit-learn`, and `statsmodels`.
- Developed as part of the CSC 380 Final Project.