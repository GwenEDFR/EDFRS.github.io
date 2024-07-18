---
description: All methods related to import data from files
---

# Import KPI

## Dependencies

| Librairies | version |
| ---------- | ------- |
| pandas     | 2.2.1   |
| datetime   | -       |
| os         | -       |

## Summary

Class for importing data from csv file and formating it for the use of this code.\
**class\_name** : import\_data, import\_E2M\_data, import\_price\_FCR

## import\_data

### **init**(self, project, year) -> None

Initialize the import\_data class.

**Parameters:**

* `self` (self): General information

* `project` (str): The project name.

* `year` (str): The year of the project.

**Returns:**

* `None` (None): No return value.

**Example:**

```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Access the attributes
print("project:", obj.project)
print("year:", obj.year)
print("year_short:", obj.year_short)
```

### main(self, data\_path)

Method to import data and format it.

**Parameters:**

* `self` (self): General information
* `data_path` (str): The path to the data file.

**Returns:**

* `df` (df): DataFrame with all formatted data.

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

### datetime\_columns(self, df)

Method to add all datetime information in the df.\
This format can be add only if column 'Date' in a format datetime is in the df in input.\
Will add :

* the **month** (in number, ex: 01 for january)\

* the **week** (in number, ex: 45 of this year)\

* the **day** (in number, ex: 18 of march)\

* the **time** (in number, ex: 18:25:35 for hours:minutes:seconde)\

* the **Date day** (in number, ex: 2024-02-18 for the 18th of february 2024)\

* the **Week day** (in number, ex 5 for saturday)\

* the **year** (in number, ex: 2024)\


**Parameters:**

* `self` (self): General information.

* `df` (df): Dataframe with all formatted data.

**Returns:**

* `df` (df): DataFrame with all formatted data.

**Example:**

```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Call the method with the dataframe 
df_with_time_columns = obj.datetime_columns(df)

# Print the formatted data
print(df_with_time_columns)
```

### import\_csv\_grafana(self, data\_path)

Method to import data from a CVS. For Grafana data.

**Parameters:**

* `self` (self): General information.
* `data_path` (str): The path to the CSV file(s).

**Returns:**

* `df` (df): DataFrame with all formatted data.

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

### import\_csv\_smartblue(self, data\_path)

Method to import data from a CVS. For smartblue data.

**Parameters:**

* `self` (self): General information.
* `data_path` (str): The path to the CSV file(s).

**Returns:**

* `df` (df): DataFrame with all formatted data.

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

### xlsx\_to\_csv(self, data\_path)

Transform .xlsx/.xls file in .csv and then delete the .xlsx file.

**Parameters:**

* `self` (self): General information.
* `data_path` (str): Path where to find the file to replace.

**Returns:**

* `none`

**Example:**

```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Call the method with the dataframe 
obj.xlsx_to_csv(data_path)

# No output 
```

### transform\_df\_TANN(self, df)

Module to normalize data from TANN to be used by this code.\
Add 0 to all 'aux 1', 'aux 2', 'aux 3', 'availability', '15 min data', 'permissible power', '\[L]', '\[AP2]', 'BESS power', '15mn average power', '15s average power', 'P', 'LMS request discharge' column (fake data).\
Add the two max on and off peak of this project (enter manually).\
Format energy in cumulative energy for the year, indeed the energy meter of Tanne reset every day that is not convenient for the computation of our KPIs.\


**Parameters:**

* `self` (self): General information.
* `df` (df): DataFrame with all formatted data.

**Returns:**

* `df` (df): DataFrame with all formatted data.

**Example:**

```python
# Create an instance of the class
obj = import_data(project="example_project", year="2022")

# Call the method with the dataframe 
formatted_df = obj.transform_df_TANN(df)

# Print the formatted data
print(formatted_df)
```

### spec_WERN_LMS(self, file_path)
Module to import data from a CSV file from the LMS in project WERN.

**Parameters:**

- `self` (self): General information.

- `file_path` (str): Path of the file 'Wernigerode_15min_data_export.csv'.

**Returns:**

- `df` (df): DataFrame with all formalized data.

**Example:**
```python
# Create an instance of the class
obj = import_data(project="WERN", year="2022")

# Specify the file path
file_path = 'path/to/Wernigerode_15min_data_export.csv'

# Call the spec_WERN_LMS method and pass the 'file_path' as an argument
result = obj.spec_WERN_LMS(file_path)

# Print the imported data as a DataFrame
print(result)
```

### transform_data_BREM_WERN(self, df)
Module to normalize data from BREM and WERN to be used by this code.

**Parameters:**

- `self` (self): General information.

- `df` (df): DataFrame with all formalized data.

**Returns:**

- `df` (df): DataFrame with all formalized data.

**Example:**
```python
# Create an instance of the class
obj = import_data(project="BREM", year="2022")

# Create a sample dataframe 'df' with formalized data
df = pd.DataFrame({
    'availability': [1, 1, 0, 1, 0],
    'other_column': [10, 20, 30, 40, 50]
    ...
})

# Call the transform_data_BREM_WERN method and pass the 'df' as an argument
result = obj.transform_data_BREM_WERN(df)

# Print the updated 'df' dataframe with the normalized data
print(result)
```

## Class import\_E2M\_data
#### \_\_init\_\_(self, project, year) -> None

Initialize the import_data class.

**Parameters:**

- `project` (str): The project name.

- `year` (str): The year of the project.

**Returns:**

- None

**Example:**
```python
from import_KPI import import_E2M_data
# Create an instance of the class
obj = import_E2M_data('ProjectName', '2022')

# Access the project and year attributes
print(obj.project)
print(obj.year)
```

### main(self)

Module to import data and format it.

**Parameters:**

- `self` (self): General information.

**Returns:**

- `df` (df): DataFrame with all formalized data.

**Example:**
```python
from import_KPI import import_E2M_data
# Create an instance of the class
obj = import_E2M_data('ProjectName', '2022')

# Call the main method
result = obj.main()

# Print the formatted data DataFrame
print(result)
```
### import_csv(self)

Module to import data from a CSV file.

**Parameters:**

- `self` (self): General information.

**Returns:**

- `df` (df): DataFrame with all formalized data.

**Example:**
```python
from import_KPI import import_E2M_data
# Create an instance of the class
obj = import_E2M_data('ProjectName', '2022')

# Call the import_csv method
result = obj.import_csv()

# Print the imported data as a DataFrame
print(result)
```

### transform_data(self, df)

Module to transform data.

**Parameters:**

- `self` (self): General information.
- `df` (df): DataFrame with all formalized data.

**Returns:**

- `df` (df): DataFrame with all formalized data.

**Example:**
```python
from import_KPI import import_E2M_data
# Create an instance of the class
obj = import_E2M_data('ProjectName', '2022')

# Call the import_csv method to get the initial DataFrame
df = obj.import_csv()

# Call the transform_data method
df_transformed = obj.transform_data(df)

# Print the transformed DataFrame
print(df_transformed)
```

### datetime_columns(self, df)

Module to add datetime columns to the DataFrame.

**Parameters:**

- `self` (self): General information.
- `df` (df): DataFrame with all formalized data.

**Returns:**

- `df` (df): DataFrame with all formalized data.

**Example:**
```python
from import_KPI import import_E2M_data
# Create an instance of the class
obj = import_E2M_data('ProjectName', '2022')

# Call the import_csv method to get the initial DataFrame
df = obj.import_csv()

# Call the transform_data method
df_transformed = obj.transform_data(df)

# Call the datetime_columns method
df_with_datetime = obj.datetime_columns(df_transformed)

# Print the transformed DataFrame with datetime columns
print(df_with_datetime)
```

## import\_price\_FCR 
### \_\_init\_\_(self) -> None

Initialize the import_price_FCR class.

**Parameters:**

- None

**Returns:**

- None

### get_price(self)

Module to get the FCR price.

**Parameters:**

- `self` (self): General information.

**Returns:**

- `dict_price` (dict): Dictionary with FCR prices.

**Example:**
```python
from import_KPI import import_price_FCR
# Create an instance of the class
obj = import_price_FCR()

# Call the get_price method
price_list = obj.get_price()

# Print the FCR prices as a dictionary
print(price_list)
```

### import_data(self)

Module to import data from an Excel file. Excel file found here : <C:\Users\******\EDF Renouvelables\EDF DS - Team Berlin - Dokumente\1. EDF DS\6.OPERATIONS\HYDRO-SPEIRA_Hamburg_211130\CONTRACTOR-SUPPLIER\FCR_e2m>
> ⚠️ File create by a human may have error/ name change. Need to be careful.
> File identify by 'TRK' only to prevent change name. 

**Parameters:**

- `self` (self): General information.

**Returns:**

- `xl` (pd.ExcelFile): Excel file object.

**Example:**
```python
# Create an instance of the class
obj = import_price_FCR()

# Call the import_data method
result = obj.import_data()

# Print the Excel file object
print(result)
```

### transform_data(self, xl)

Module to transform data from the Excel file.

**Parameters:**

- `self` (self): General information.

- `xl` (pd.ExcelFile): Excel file object.

**Returns:**

- `dict_price` (dict): Dictionary with transformed price data.

**Example:**
```python
# Create an instance of the class
obj = import_price_FCR()

# Call the import_data method to get the Excel file object
xl = obj.import_data()

# Call the transform_data method
result = obj.transform_data(xl)

# Print the transformed price data as a dictionary
print(result)
```