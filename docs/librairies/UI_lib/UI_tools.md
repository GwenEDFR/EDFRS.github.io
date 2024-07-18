# UI tools
## Dependencies
|Librairies | version|
|-----------|--------|
|pandas| - |
|shutil| - |

## Summary
Methods used by the UI for simple tasks. 


## Methods
### get_month_df(database)
Used to get the list of month present in the database. 

**Parameters:**

* `database` (df): Database where the column month is. 

**Returns:**

* `list_month` (array): List of months inside the dataframe

**Examples:**
```py
import UI_tools 
# Create a sample database
data = {'month': [1, 2, 3, 4, 3, 2, 2, 4]}
sales_data = pd.DataFrame(data)

# Call the function with the sales_data database
unique_months = UI_tools.get_month_df(sales_data)

# Print the unique months
print(unique_months)
>> ['1','2','3','4']
```

### clear_folder(path, noFile_ok=False)

Clears the file or folder in the given path.

**Parameters:**

- `path` (str): Path to clear.

- `noFile_ok` (bool, default: False): Raises an error if there are no files/folders in the path if set to False.

**Returns:**

None

**Raises:**

- `ValueError`: If `noFile_ok` is set to False and there are no files or folders in the path.

**Examples:**
```py 
import UI_tools
# Example usage
folder_path = "path/to/folder"
UI_tools.clear_folder(folder_path, noFile_ok=True)

# If the folder path is not a file or a folder
UI_tools.clear_folder(folder_path, noFile_ok=False)
>> ValueError: file path/to/folder is not a file or dir.
```