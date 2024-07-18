# HLZ
## Dependencies
|Librairies | version|
|-----------|--------|
|numpy| 1.26.4 |
|datetime | - |

## Summary
Class for the creation of the period FCR, on peak, off peak of each project.<br/>
**class_name** : set_period

## Set_period
### \_\_init\_\_(self, project:str, year) -> None
Initialize the class.

**Parameters:**

- `self` (self): General information

- ``project`` (str): The project name.
            
- ``year`` (str): The year of the project.

**Returns:**

- `None` (None):
    No return value.

**Example:**
```python
# Create an instance of the class
obj = HLZ.set_period('HYHA', '2024')

# Access the attribute
print("project selected:", obj.project)
```
### main(self, database)
Add the period time in the project. Compute automaticaly the On peak period and the FCR bid. If data from E2M available (folder E2M in data) compare the real bid registered. 

**Parameters:**

- `self` (self): General information

- ``database`` (df): Database of the selected project.

**Returns:**

- ``database`` (df): Database of the selected project with HLZ period. Add in the HLZ column.

**Example:**
```python
# Create an instance of the class
obj = HLZ.set_period('HYHA', '2024')

# Call the method
df = obj.main(database)

print("HLZ of this project:", df['HLZ'])
```

### mask_period(self, df, database)
Create the mask for period on this project

**Parameters:**

- `self` (self): General information

- ``df`` (df): With all informations for On peak and FCR mask

- ``database`` (df): Database of the selected project.

**Returns:**

- ``database`` (df): Database of the selected project with HLZ period. Add in the HLZ column.

**Example:**
```python
# Create an instance of the class
obj = HLZ.set_period('HYHA', '2024')

# Create a sample dataframe 'df' with information for On peak and FCR mask
df = pd.DataFrame({
    'On-Peak Start': [time(8, 0), time(13, 0)],
    'On-Peak Stop': [time(10, 0), time(15, 0)],
    'FCR_slots': [time(9, 0), time(14, 0)],
    'month': [1, 2]
})

# Create a sample dataframe 'database' with the selected project's database
database = pd.DataFrame({
    'Date': pd.date_range(start='1/1/2022', periods=10),
    'Value': [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
})

# Call the mask_period method and pass the 'df' and 'database' as arguments
result = obj.mask_period(df, database)

# Print the updated 'database' dataframe with the 'HLZ' column added
print(result)
```

### get_On_peak_hours(self)
Read the On peak hours from overview and format it.

**Parameters:**

- `none`: No parameters required.

**Returns:**

- `on_peak_start` (np.array): Array with start On peak period.

- `on_peak_stop` (np.array): Array with stop On peak period.

**Example:**
```python
# Create an instance of the class
obj = HLZ.set_period('HYHA', '2024')

# Call the get_On_peak_hours method
start_times, stop_times = obj.get_On_peak_hours()

# Print the start and stop times
print(start_times)
print(stop_times)
```

### get_FCR_hours(self, df)
Compute the FCR slot hours, regarding the On peak hours.

**Parameters:**

- `df` (df): DataFrame with all information for On peak and FCR mask.

**Returns:**

- `df` (df): DataFrame with all information for On peak and FCR mask + FCR slot column.

**Example:**
```python
# Create an instance of the class
obj = HLZ.set_period('HYHA', '2024')

# Create a sample dataframe 'df' with information for On peak and FCR mask
df = pd.DataFrame({
    'On-Peak Start': [time(8, 0), time(13, 0)],
    'On-Peak Stop': [time(10, 0), time(15, 0)]
})

# Call the get_FCR_hours method and pass the 'df' as an argument
result = obj.get_FCR_hours(df)

# Print the updated 'df' dataframe with the 'FCR_slots' column added
print(result)
```

### double_verification_E2M(self, database)
Module to correlate new (& real) HLZ period from E2M data. Only replace the data available in E2M csv.<br>

> ⚠️ Data from E2M may be not accurate... (Issues from Mars 2024)

**Parameters:**

- `self` (self): General information.

- `database` (df): DataFrame with all formalized data.

**Returns:**

- `df` (df): DataFrame with all formalized data verified by E2M data.

**Example:**
```python
# Create an instance of the class
obj = HLZ.set_period('HYHA', '2024')

# Create a sample dataframe 'database' with formalized data
database = pd.DataFrame({
    'Date': pd.date_range(start='1/1/2022', periods=10),
    'HLZ': ['off peak', 'off peak', 'FCR', 'on peak', 'off peak', 'FCR', 'on peak', 'off peak', 'on peak', 'FCR']
})

# Call the double_verification_E2M method and pass the 'database' as an argument
result = obj.double_verification_E2M(database)

# Print the updated 'database' dataframe with the HLZ period verified by E2M data
print(result)
```