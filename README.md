# iot-sensor-data-pipeline
# Build a Data Ingestion and Transformation Script for Sensor Data

## Description
This repository contains a Jupyter Notebook (`process_sensor_data.ipynb`) that processes raw, continuous IoT sensor data streams. It reads a messy sample dataset, cleans the data based on specific rules, and outputs a structured CSV ready for analysis.

## Repository Structure
* `raw_sensor_data.csv`: The initial messy sample dataset containing errors.
* `process_sensor_data.ipynb`: The main Jupyter Notebook containing the data ingestion and transformation pipeline, along with execution logs.
* `cleaned_sensor_data.csv`: The final, clean dataset outputted by the pipeline.
* `README.md`: Project documentation.

## Processing Steps
When the notebook is executed, it applies the following data transformation rules:
1. **Duplicates:** Identifies and drops exact duplicate rows.
2. **Missing Values:** * Drops any records missing critical metadata (e.g., `sensor_id`).
   * Imputes missing sensor `value` readings using the median value of that specific `sensor_type`.
3. **Outliers:** Removes obvious sensor errors by dropping values that fall outside realistic physical boundaries (e.g., filtering out `999.9` error codes).
4. **Transformation:** Converts string timestamps into proper datetime objects and sorts the final dataset chronologically.

## How to Run
1. Ensure you have Python installed along with the `pandas` and `jupyter` libraries.
2. Open `process_sensor_data.ipynb` in your Jupyter environment.
3. Ensure `raw_sensor_data.csv` is in the exact same directory.
4. Run the cells to execute the script. Watch the log output to track the cleaning process.
5. Open the newly generated `cleaned_sensor_data.csv` to view the results.
