# Export KPI

## Dependencies
|Librairies | version|
|-----------|--------|
|KPI_plot.py (local)| - |
|parameters_project.py (local)| - |
|inspect | - |
|pandas| 2.2.1 |
|pathlib.Path| - |
|plotly.io.pio| 5.20.0 |
|os| - |
|tqdm.tqdm| 4.66.2 |

## Summary
Class create png from KPIs plot. Use the KPI_plot.py library to generate the data. 
Normal size of an image 1200x800 px.<br/>
**class_name** : export_data

## Methods
### _ _init_ _(self, database, project, year) -> None
Initializes an instance of the class.<br/>
**Parameters:**

- `database` (str): The name of the database.

- `project` (str): The name of the project.

- `year` (str): The year for the project.

**Returns:**  

- `nan` (None) :
    No return value

**Example:**  
```python
# Create an instance of the class
database = "example_database"
project = "example_project"
year = "2022"
obj = export_data(database, project, year)

# Access the attributes
print("database:", obj.database)
print("project:", obj.project)
print("year:", obj.year)
print("year_short:", obj.year_short)
```

### get_methods(self)
Intern Module to get all name of methods from KPI_plot.

**Parameter:**

- `self` (self) :
    General information

**Returns:**

- `fig_store` (df) :
    DataFrame with names and categories of KPI

- `plot_method` (array) :
    Array with all methods from KPI_plot module

- `def_plot` (module) :
    Module of plot_KPI in order to get the methods from it

**Example:**  
```python
# Create an instance of the class
obj = export_data(database, project, year)

# Call the get_methods method
fig_store, plot_method, def_plot = obj.get_methods()

# Print the results
print("fig_store:", fig_store)
print("plot_method:", plot_method)
print("def_plot:", def_plot)
```

### export_KPI(self, width=1200, height=800, scale=2)
Module to export data and format it.

**Parameters:**

- `self` (self) :
    General information

- `width` (int) :
    Width of the png, default = 1200 px

- `height` (int) :
    Height of the png, default = 800 px

- `scale` (int) :
    Scale of the final export, default = 2

**Returns:**

- `nan` (None) :
    No return value

**Example:**

```python
# Create an instance of the class
obj = export_data(database, project, year)

# Call the export_KPI method
obj.export_KPI(width=1000, height=600, scale=3)
```

### show_KPI(self)
Module to show plot from data and format it.

**Parameter:**

- `self` (self) :
    General information

**Returns:**

- `nan` (None) :
    No return value

**Example:**  
```python
# Create an instance of the class
obj = export_data(database, project, year)

# Call the show_KPI method
obj.show_KPI()
```