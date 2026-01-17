NFL PlayerProfiler Data Scraper

This Jupyter notebook provides a script to scrape performance data for NFL players from playerprofiler.com for the 2020 season, process it using Pandas, and save the resulting DataFrame to a CSV file in Google Drive.

This script automates the process of collecting detailed performance metrics for NFL skill position players. It fetches a list of all players, filters for each positionr, and then iterates through each position to retrieve their season performance data. The collected data is then organized into a pandas DataFrame and saved as a CSV file.

Prerequisites
To run this notebook, you need the following Python libraries installed:

pandas
requests
You can install them using pip if you haven't already:

pip install pandas requests
Additionally, access to Google Drive is required for saving the output file.

Code Description
1. Initial Setup and Imports
This section imports necessary libraries (pandas, requests, google.colab.drive) and sets up warning filters.

2. Fetching Player IDs
This cell makes an API call to playerprofiler.com to get a list of all player IDs and their basic information. It then filters this list to only include players with the position.

3. Collecting Detailed Performance Metrics
This is the core data collection section. It iterates through each identified running back, makes a specific API call for each player to retrieve their performance metrics for the desired season, and appends the relevant data to a list of dictionaries. Finally, it converts this list into a pandas DataFrame.

4. Displaying the DataFrame
This cell simply displays the head of the generated DataFrame to give a preview of the collected data.

5. Mounting Google Drive
This command mounts your Google Drive to the Colab environment, allowing the notebook to read from and write to your Drive.

6. Saving Data to CSV
This final cell saves the collected DataFrame as a CSV file  into the 'My Drive' root directory of your Google Drive.

Output
The script generates a CSV file  containing comprehensive performance metrics for NFL running backs from the desired season. The DataFrame includes various statistics.


Causal Inference in Fantasy Football (Work in Progress)

Introduction
This notebook aims to apply causal inference techniques, specifically using the DoWhy library, to understand the causal relationships between various player performance metrics and Fantasy Football Points (FPTS). The goal is to move beyond mere correlations and identify true causal effects that can inform better fantasy football decision-making.

Current Status
As of now, the notebook includes the following functionalities:

Causal Graph Definition: A Directed Acyclic Graph (DAG) representing hypothesized causal relationships between numerous fantasy football metrics (e.g., RUSH_AGE, RushYds/Att, SNAP_SHARE, FPTS, etc.) has been defined.
Data Loading: A load_data function is available to load player data from a CSV file.
Data Validation: A validate_data function checks if the loaded DataFrame contains all expected columns based on the causal graph.
Robust Data Preprocessing: A preprocess_data_robust function handles missing values using imputation (mean for numerical, most frequent for categorical) and scales numerical features using StandardScaler while encoding categorical features using OneHotEncoder.
Causal Effect Identification: Functions to identify the causal estimand using DoWhy's identify_effect method.
Causal Effect Estimation: Functions to estimate the causal effect using DoWhy's estimate_effect method, with backdoor.linear_regression as the default.
Training and Evaluation Workflow: A train_and_evaluate_model function orchestrates the causal inference process from model initialization to estimation.
Main Execution Block: A if __name__ == "__main__" block demonstrates the end-to-end workflow, from creating the graph to loading, preprocessing, and analyzing a sample causal effect (e.g., RUSH_ATT on FPTS).
Usage
To use this notebook:

Provide Data: Update the file_path variable in the main execution block with the path to your fantasy football dataset (CSV format).
Define Treatment and Outcome: In the main execution block, set treatment_variable and outcome_variable according to the causal effect you wish to analyze.
Run the Notebook: Execute the cells sequentially.
Next Steps / Future Work
Refine Causal Graph: Continuously review and potentially update the causal graph based on domain expertise and further data exploration.
Data Integration: Implement more robust data loading and merging strategies if data comes from multiple sources.
Robustness Checks: Integrate DoWhy's built-in refuters and sensitivity analysis methods to validate the causal estimates.
Exploratory Data Analysis (EDA): Add more comprehensive EDA to understand data distributions, correlations, and potential issues before causal analysis.
Advanced Estimation Methods: Experiment with different causal estimation methods provided by DoWhy (e.g., G-formula, IV methods) and compare their results.
Intervention and Policy Evaluation: Explore how to simulate interventions and evaluate their potential impact on FPTS.
Visualization: Visualize the causal graph and causal effects more effectively.
Documentation: Add more detailed comments and explanations throughout the code.
Dependencies
pandas
numpy
networkx
dowhy
scikit-learn
Data Schema
The notebook expects a dataset with columns corresponding to the nodes in the causal graph. A detailed data schema and preprocessing notes are available in the notebook's markdown cells.
