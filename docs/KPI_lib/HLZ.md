# HLZ
## Dependencies
|Librairies | version|
|-----------|--------|
|numpy| 1.26.4 |
|datetime | - |

## Summary
Class for the creation of the period FCR, on peak, off peak of each project.<br/>
**class_name** : [BREM](#methods-class-brem) [HYHA](#methods-class-hyha)

## Methods Class BREM
### __init__(self, df) -> None
Initialize the class.

**Parameters:**

- `self` (self):
    General information

- `df` (df):
    The DataFrame to be assigned.

**Returns:**

- `None` (None):
    No return value.

**Example:**
```python
# Create a DataFrame
df = pd.DataFrame({'SOC': [1, 2, 3], '15 min data': [4, 5, 6]})

# Create an instance of the class
obj = ClassName(df)

# Access the attribute
print("df:", obj.df)
```


### y_2024(self)
Method to create HLZ for a certain project.  
**HLZ 2024**  

| Winter | Spring  | Summer | Autumn |
| -------| --------| -------| ------ |
| 09:30 - 15:15<br/>16:00 - 19:15   | -------- | -------- | 11:00 - 13:00  |

**Parameter:**

- `self` (self):
    General information

**Returns:**

- `HLZ column` (df):
    Insert this HLZ column to your dataframe, all information of 'on peak', 'off peak', 'FCR' period.

**Example:**
```py
# Create an instance of the class
obj = BREM()

# Call the y_2024 method
hlz_column = obj.y_2024()

# Print the HLZ column
print(hlz_column)
```
## Methods Class HYHA
### __init__(self, df) -> None
Initialize the class.

**Parameters:**

- `self` (self):
    General information

- `df` (df):
    The DataFrame to be assigned.

**Returns:**

- `None` (None):
    No return value.

**Example:**
```python
# Create a DataFrame
df = pd.DataFrame({'SOC': [1, 2, 3], '15 min data': [4, 5, 6]})

# Create an instance of the class
obj = ClassName(df)

# Access the attribute
print("df:", obj.df)
```


### y_2024(self)
Method to create HLZ for a certain project.  
**HLZ 2024**  

| Winter | Spring  | Summer | Autumn |
| --------------- | --------------- | --------------- | --------------- |
| 09:30 - 19:30    | 10:45 - 13:00  | -------- | 10:00 - 16:15<br/>18:15 - 19:15 


**Parameter:**

- `self` (self):
    General information

**Returns:**

- `HLZ column` (df):
    Insert this HLZ column to your dataframe, all information of 'on peak', 'off peak', 'FCR' period.

**Example:**
```py
# Create an instance of the class
obj = HYHA()

# Call the y_2024 method
hlz_column = obj.y_2024()

# Print the HLZ column
print(hlz_column)
```

### y_2023(self)
Method to create HLZ for a certain project.  
**HLZ 2023**  

| Winter | Spring  | Summer | Autumn |
| --------------- | --------------- | --------------- | --------------- |
| 09:00 - 19:15    | -------- | -------- | 8:00 - 15:45 <br>16:45 - 19:00|


**Parameter:**

- `self` (self):
    General information

**Returns:**

- `HLZ column` (df):
    Insert this HLZ column to your dataframe, all information of 'on peak', 'off peak', 'FCR' period.

**Example:**
```py
# Create an instance of the class
obj = HYHA()

# Call the y_2024 method
hlz_column = obj.y_2023()

# Print the HLZ column
print(hlz_column)
```