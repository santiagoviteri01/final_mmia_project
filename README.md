Final Project - Fantasy Premier League Forecasting
This repository contains the code and data needed to run forecasts and simulate results for Fantasy Premier League (FPL). Follow these instructions to set up the environment, run the models, and replicate the results.

Table of Contents
Project Overview
Prerequisites
Setup Instructions
Running the Model
Subsequent Runs
Final Adjustments
Generating Results and Analysis
Summary
Project Overview
The purpose of this project is to forecast player and team performance for upcoming FPL gameweeks based on historical data. The project includes multiple models, data preparation, and custom predictions to help you optimize FPL decisions.

Prerequisites
Download Required Files:
fpl.zip: Contains all the datasets needed for model training and predictions.
Notebook Files (.ipynb): Download both notebooks provided in this repository.
Setup Instructions
Step 1: Environment Setup
Download and extract fpl.zip to your local machine. This folder includes the datasets necessary to replicate the project’s results.
Ensure that both .ipynb files (the main notebooks) are in the same directory as the extracted datasets for seamless access.
Running the Model
Step 2: Initial Model Run
Open the first notebook and run all cells from the beginning up to the section labeled "Dataset for the first model:".
Continue running all cells sequentially for the first full run.
Important Code Modification
For the initial run:
Run all cells in order without modification.
For subsequent runs:
Uncomment the following lines in the notebook:
python
Copy code
# After the first run, uncomment the following lines:
# n = 1
# delta = 3 * n + (n - 1)
# df_1_2023_2024_m = df_1_2023_2024[df_1_2023_2024["GW"] <= (min(df_1_2023_2024["GW"] + 3))]
# df_combined = pd.concat([df_1_2016_2017, df_1_2017_2018, df_1_2018_2019, df_1_2019_2020, df_1_2020_2021, df_1_2021_2022, df_1_2022_2023, df_1_2023_2024_m], ignore_index=True)
Run the "Dictionaries" Section: Run this to set up the required data mappings.

Forecast Section:

Run the Re-training and Predicting subsection to generate a forecast file with total points and values.
Subsequent Runs
After the initial run, you will need to repeat this process for different values of n (1, 2, 4, 5,...,9.):

Data Preparation: Run the Data Preparation and First Run of the Fantasy Team sections.

This will generate two CSV files:
gameweek_solutions_1_4_2023_2024.csv
df_1_4.csv
For each new prediction, adjust n and ensure you’ve added the previous gameweek solutions to your working directory.

Final Adjustments
When n=9, forecast only two gameweeks: GW 37 and GW 38.

Set:

val_1 = 37
val_2 = 38
In the Training and Predicting section:

Update:
python
Copy code
forecast = forecast_future(best_model, combined_data, data_module.n_steps, n_forecast=2)
In the Data Preparation section:
python
Copy code
filtered_df_c_2['GW'] = filtered_df_c_2['GW'].replace({1: val_1, 2: val_2})
Generating Results and Analysis
Run the Actual vs Real Comparison section. This will create a CSV file for final analysis.
Analysis Section: Use the generated file to analyze and interpret the project’s results.
