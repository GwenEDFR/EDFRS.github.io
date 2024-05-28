# Import KPI

## Dependencies
|Librairies | version|
|-----------|--------|
|pandas| 2.2.1 |
|datetime | - |
|os | - |

## Summary
Class for importing data from csv file and formating it for the use of this code.<br/>
**class_name** : import_data

## Methods

### __init__(self, project, year) -> None
Initialize the import_data class.

**Parameters:**

- `self` (self):
    General information

- `project` (str):
    The project name.

- `year` (str):
    The year of the project.

**Returns:**

- `None` (None):
    No return value.

**Example:**
```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Access the attributes
print("project:", obj.project)
print("year:", obj.year)
print("year_short:", obj.year_short)
```

### main(self, data_path)
Method to import data and format it.

**Parameters:**

- `self` (self):
    General information

- `data_path` (str):
    The path to the data file.

**Returns:**

- `df` (df):
    DataFrame with all formatted data.

**Example:**

```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Call the main method with the data path
data_path = "path/to/data.csv"
formatted_data = obj.main(data_path)

# Print the formatted data
print(formatted_data)
```

### datetime_columns(self, df)
Method to add all datetime information in the df.  
This format can be add only if column 'Date' in a format datetime is in the df in input.<br>
Will add :  
- the **month** (in number, ex: 01 for january)<br>
- the **week** (in number, ex: 45 of this year)<br>
- the **day** (in number, ex: 18 of march)<br>
- the **time** (in number, ex: 18:25:35 for hours:minutes:seconde)<br>
- the **Date day** (in number, ex: 2024-02-18 for the 18th of february 2024)<br>
- the **Week day** (in number, ex 5 for saturday)<br>
- the **year** (in number, ex: 2024)<br>

**Parameters:**

- `self` (self):
    General information.

- `df` (df):
    Dataframe with all formatted data.

**Returns:**

- `df` (df):
    DataFrame with all formatted data.

**Example:**
```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Call the method with the dataframe 
df_with_time_columns = obj.datetime_columns(df)

# Print the formatted data
print(df_with_time_columns)
```

### import_csv_grafana(self, data_path)
Method to import data from a CVS. For Grafana data. 

**Parameters:**

- `self` (self):
    General information.

- `data_path` (str):
    The path to the CSV file(s).

**Returns:**

- `df` (df):
    DataFrame with all formatted data.

**Example:**
```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Call the import_csv method with the data path
data_path = "path/to/data.csv"
formatted_data = obj.import_csv_grafana(data_path)

# Print the formatted data
print(formatted_data)
```

### import_csv_smartblue(self, data_path)
Method to import data from a CVS. For smartblue data. 

**Parameters:**

- `self` (self):
    General information.

- `data_path` (str):
    The path to the CSV file(s).

**Returns:**

- `df` (df):
    DataFrame with all formatted data.

**Example:**
```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Call the import_csv_smartblue method with the data path
data_path = "path/to/data.csv"
formatted_data = obj.import_csv_smartblue(data_path)

# Print the formatted data
print(formatted_data)
```

### xlsx_to_csv(self, data_path)
Transform .xlsx/.xls file in .csv and then delete the .xlsx file. 

**Parameters:**

- `self` (self):
    General information.

- `data_path` (str):
    Path where to find the file to replace.

**Returns:**

- `none`

**Example:**
```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Call the method with the dataframe 
obj.xlsx_to_csv(data_path)

# No output 
```

### transform_df_TANN(self, df)
Module to normalize data from TANN to be used by this code.<br>
Add 0 to all 'aux 1', 'aux 2', 'aux 3', 'availability', '15 min data', 'permissible power', '[L]', '[AP2]', 'BESS power', '15mn average power', '15s average power', 'P', 'LMS request discharge' column (fake data).<br>
Add the two max on and off peak of this project (enter manually).<br>
Format energy in cumulative energy for the year, indeed the energy meter of Tanne reset every day that is not convenient for the computation of our KPIs.<br> 

**Parameters:**

- `self` (self):
    General information.

- `df` (df):
    DataFrame with all formatted data.

**Returns:**

- `df` (df):
    DataFrame with all formatted data.

**Example:**
```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Call the method with the dataframe 
formatted_df = obj.transform_df_TANN(df)

# Print the formatted data
print(formatted_df)
```