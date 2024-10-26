# Final Project Instructions

This guide provides a step-by-step explanation of how to set up and run the final project for replicating results.

## Prerequisites

Download the following files:

- **`fpl.zip`**: This archive contains all the datasets needed for the project.
- **Notebook files**: Download both `.ipynb` files provided in this repository.

## Instructions

### Step 1: Setup

1. Download and extract `fpl.zip` to your local machine.
2. Ensure both `.ipynb` files are available in the same working directory as the extracted dataset.

### Step 2: Run the First Model Notebook

1. Run the notebook from the beginning and complete the first model execution.
2. Follow these guidelines during execution:
   - **For the initial run**:
     - Run all cells up to **"Dataset for the first model:"**.
   - **For subsequent runs**:
     - Uncomment the following lines and adjust the variables as explained:
       ```python
       # After the first run, uncomment the following line and change the variable delta by 3*n + (n-1), where n = 1, 2, 4, 5, 6, 7, 8, 9.
       # n = 1
       # delta = 3 * n + (n - 1)
       # df_1_2023_2024_m = df_1_2023_2024[df_1_2023_2024["GW"] <= (min(df_1_2023_2024["GW"] + 3))]
       # df_combined = pd.concat([df_1_2016_2017, df_1_2017_2018, df_1_2018_2019, df_1_2019_2020, df_1_2020_2021, df_1_2021_2022, df_1_2022_2023, df_1_2023_2024_m], ignore_index=True)
       ```
3. Run the **dictionaries section**, followed by **Re-training and Predicting** within the **Forecast** section.
   - A file with forecasts for total points and values will be created at this stage.

### Step 3: First Prediction Run

- **Data Preparation**:
  - Once you have the first predictions, continue by running the **Data Preparation** and **First Run of the Fantasy Team** sections.
  - This will generate two CSV files:
    - `gameweek_solutions_1_4_2023_2024.csv`
    - `df_1_4.csv`

### Subsequent Runs

- For each new run, repeat the steps as above, modifying the variable `n` as follows:
  - If `n = 2`, ensure the `gameweek_solutions_1_4_2023_2024.csv` and `df_1_4.csv` files are in the working directory.
  - Use these files for each new prediction until you reach `n=9`.

### Step 4: Final Adjustments and Predictions

- When `n=9`, you'll be forecasting only two gameweeks: GW 37 and GW 38.
- Adjust `val_1` to 37 and `val_2` to 38 in your code.

- In the **Training and Predicting** section:
  ```python
  forecast = forecast_future(best_model, combined_data, data_module.n_steps, n_forecast=2)
  ```
- In the **Data Preparation** section:
    ```python
    - filtered_df_c_2['GW'] = filtered_df_c_2['GW'].replace({1: val_1, 2: val_2})
    - filtered_df_p_2['GW'] = filtered_df_p_2['GW'].replace({1: val_1, 2: val_2})
  ```

