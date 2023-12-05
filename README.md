```python
# Guardian API Data Extraction and Loading

## Overview

This Python script utilizes the Guardian API to extract articles related to "AI," "analytics," and "data." The extracted data is then cleaned, processed, and loaded into a PostgreSQL database. The process involves making API calls, retrieving article information, handling data in DataFrames, and eventually loading the cleaned data into a PostgreSQL database.

## Prerequisites

Before running the script, ensure you have the required libraries installed:

- numpy
- pandas
- datetime
- sys
- requests
- math
- sqlalchemy

Make sure to install these libraries using:

```bash
pip install numpy pandas sqlalchemy requests
```

## Configuration

1. **Database Connection:**
   - The script connects to a PostgreSQL database. Update the `create_engine` line to reflect your PostgreSQL database connection details.

   ```python
   engine = create_engine('postgresql://your_username:your_password@localhost:5432/your_database_name')
   ```

2. **Guardian API Key:**
   - You need a Guardian API key to make requests. Replace the `api_key` variable with your own API key.

   ```python
   api_key = 'your_guardian_api_key'
   ```

3. **Search Query and Parameters:**
   - Adjust the `search_query`, `total_articles`, `page_size`, and other parameters according to your requirements.

   ```python
   search_query = 'AI AND analytics AND data'
   total_articles = 100
   page_size = 50
   ```

## Execution

1. **Run the Script:**
   - Execute the script in a Jupyter Notebook or a Python environment.

   ```python
   %run your_script_name.py
   ```

2. **Review Output:**
   - The script prints information about the selected pages and the total number of results.
   - Two CSV files (`guardian_original_.csv` and `guardian_final_.csv`) are created: one with the original data and the other with cleaned and filtered data.

3. **Data Manipulations:**
   - The script includes several data manipulations using pandas:
     - Sorting the data by `webPublicationDate` in descending order.
     - Creating a new column `formatted_date` showing the date in `dd/mm/yyyy` format.
     - Creating a new column `year` showing the date in `yyyy` format.
     - Filtering the data to include only articles with 1000 words or more.
     - Formatting all column names to snake_case.

4. **Load Data into PostgreSQL:**
   - The script includes a function `etl_guardian` to load the final data into a PostgreSQL database. Adjust the function parameters as needed and run it.

   ```python
   etl_guardian(chunk_size=100, table_name='guardian_final_', connection=engine)
   ```

## Notes

- Handle any errors that may occur during the API call or data loading process.
- Ensure the PostgreSQL database is properly configured and accessible.

Feel free to customize the script according to your specific needs or integrate it into a larger data pipeline.
```
