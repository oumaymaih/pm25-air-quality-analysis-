# PM2.5 Air Quality Exploratory Analysis — Ben Guerir, Morocco

## Project Overview

This project explores hourly air-quality measurements from the ARC Air monitoring station in Ben Guerir, Morocco. The analysis focuses on PM2.5 concentrations, their temporal variability, high-concentration observations, and their associations with other measured variables.

The notebook includes:
- dataset inspection and data-quality checks;
- transformation from long format to wide format;
- descriptive statistics and PM2.5 distribution;
- temporal visualization and investigation of high-concentration observations;
- correlation analysis with temperature, relative humidity, PM1, and `um003`;
- comparison of PM2.5 concentrations across broad periods of the day.

This is an exploratory data analysis project. A Machine Learning model is proposed as future work; predictive modelling is not implemented in this notebook.

## Data Source

**Source:** OpenAQ — ARC Air monitoring location, Ben Guerir, Morocco  
**Location ID:** `3847229`  
**Station page:** https://explore.openaq.org/locations/3847229

### How the dataset was obtained

The CSV used for this analysis was downloaded manually from the OpenAQ station page:

1. Open the [ARC Air location page on OpenAQ](https://explore.openaq.org/locations/3847229).
2. Sign in to an OpenAQ account, if prompted.
3. Select **Download data**.
4. Set the desired date range, starting on **1 June 2026** to **12 July 2026**
5. Download the CSV export.
> **Data coverage:** The downloaded CSV contains 5,000 measurement records across five parameters, covering 1 June to 12 July 2026, based on the timestamps in the file. Although a later end date was selected in OpenAQ Explorer, the export returned 1,000 records per parameter. This may reflect the platform's export limit. For larger downloads, OpenAQ recommends using its API.

The notebook was developed using the resulting file:

`openaq_location_3847229_measurments_mois6_mois10.csv`

The analysed records cover **1 June to 12 July 2026**, based on the timestamps in the exported file. The export contains 5,000 measurement rows across five parameters, corresponding to 1,000 unique timestamps at the ARC Air location.

**Reproducibility note:** OpenAQ exports can change as data are added or corrected. A newly downloaded export may not match the original file exactly. For the closest reproduction, use the same date range and retain the downloaded CSV used for this analysis. Check OpenAQ's applicable terms and data licensing before redistributing the file.

## How to Run the Notebook

The notebook is designed for **Google Colab**.

1. Download the CSV from the OpenAQ station page using the steps above.
2. Upload the CSV to the root of your Google Drive (`My Drive`), or note the folder where you save it.
3. Open `PM25_Exploratory_Analysis_Final.ipynb` in Google Colab.
4. Run the setup cell and authorize Colab to access your Google Drive.
5. Ensure that `FILE_PATH` in the data-loading cell points to the CSV's actual location. By default, the notebook expects:

   `/content/drive/MyDrive/openaq_location_3847229_measurments_mois6_mois10.csv`

6. Run the notebook from top to bottom using **Runtime → Run all**.

If you saved the CSV in a subfolder or used a different filename, update `FILE_PATH` before running the data-loading cell.

## Main Research Questions

- How do PM2.5 concentrations vary over time?
- How are PM2.5 concentrations associated with temperature and relative humidity?
- How strongly are PM2.5 concentrations associated with PM1 and `um003`?
- Do average PM2.5 concentrations differ across broad periods of the day?

## Tools

- Python
- pandas
- NumPy
- Matplotlib
- Google Colab

## Key Findings

The exploratory analysis found substantial variation in PM2.5 concentrations, including several pronounced high-concentration observations. PM2.5 showed a weak negative association with temperature and a positive association with relative humidity. PM1 and `um003` were very strongly correlated with PM2.5. Average PM2.5 concentrations were highest in the morning and lowest in the evening in this dataset.

These are descriptive and correlational findings. They do not establish causation, and the observed daily differences should not be interpreted as a confirmed recurring pattern without further analysis.

## Limitations and Future Work

- The analysis covers one monitoring location and a relatively short observation period.
- Correlation does not establish causation.
- High-concentration observations require further investigation; they should not be removed automatically.
- The meaning of `um003` should be confirmed using the relevant sensor documentation.
- Future work could use longer time series and additional locations, examine pollution episodes, and design and evaluate a Machine Learning model to forecast PM2.5 using predictors available at forecast time.

## Repository Contents

- `PM25_Exploratory_Analysis.ipynb` — notebook containing the analysis.
- `README.md` — project description, data-source information, and reproduction instructions.

The raw CSV is not included in this repository by default. Please obtain it from the linked OpenAQ source and review the applicable data terms before sharing a copy.
