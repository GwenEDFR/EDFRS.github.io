# UI projects 
## Dependencies
|Librairies | version|
|-----------|--------|
|pandas| - | 

## Class project_init

A class used for initializing a project.

#### __init__(self, project, year)

Initialize the `project_init` class.

**Parameters:**

- `project` (str): The project name.

- `year` (str): The year of the project.

**Returns:**

None

#### init_start(self, data_path)

Initialize the project by importing data and setting the HLZ.

**Parameters:**

- `self` (self): General information.

- `data_path` (str): Path to the data.

**Returns:**

- `database` (df): Database with all information of this project.

- `first_data_time` (date): Date of the first data of the database.

- `last_data_time` (date): Date of the last data of the database.

**Example:**
```py
from project import project_init
project = "Sample Project"
year = "2022"
data_path = "path/to/data"
# Call the method
project_obj = project_init(project, year)
database, first_data_time, last_data_time = project_obj.init_start(data_path)

#Print the result
print(database)
print(first_data_time)
print(last_data_time)
```