# FCR class
## __init__ (self, database, period)
Initialize the class.

**Parameters:**

- `self` (self):
    General information

- `database` (df):
    The DataFrame representing the database.

**Returns:**

- `None` (None):
    No return value.

**Example:**
```py
from KPI import FCR
# Create a DataFrame representing the database
database = pd.DataFrame({'SOC': [1, 2, 3], '15 min data': [4, 5, 6]})

# Create an instance of the class
obj = FCR(database, "2022")

# Access the attributes
print("df:", obj.df)
print("period:", obj.period)
```

## event_count (self)
Method for finding all discharge/charge events that appear in the selected period. <br>
/!\ Improvement to do for the selection, need to integer FCR label.

**Parameter:**

- `self` (self): Dataframe general, period

**Returns:**

- `Date Day` (datetime): Date of the day

- `week` (int): Week number

- `Week day` (int): Number of the day in the week (0 = Monday, ... , 6 = Sunday)

- `month` (int): Month number of the date

- `SOC` (float): State of Charge associated with this event

- `type` (str): Type of the selected row (charge/discharge)

- `discharge` (int): 1 in the row if it is a discharge event

- `charge` (int): 1 in the row if it is a charge event

**Example:**
```py
from KPI import FCR
# Create an instance of your class
my_instance = FCR(database, "2022")

# Call the event_count method
result = my_instance.event_count()

# Print the result
print(result)
```
## event_day_after_schedule (self, event)
Method for finding all discharge/charge events that appear in the selected period. <br>
Sorted by day after schedule (description still to be done).

**Parameters:**

- `self` (self): Dataframe general, period

- `event` (df): DataFrame with all found events

**Returns:**

- `Week day` (int): Number of the day in the week (0 = Monday, ..., 6 = Sunday)

- `month` (int): Month number of the date

- `discharge` (int): 1 in the row if it is a discharge event

- `charge` (int): 1 in the row if it is a charge event

- `day after scheduling event` (int): 1 if the selected row (=day) is counted as a day after schedule

**Example:**
```py
from KPI import FCR
# Create an instance of your class
my_instance = FCR(database, "2022")

# Assuming you already have the `event` DataFrame from the previous method
# Call the event_day_after_schedule method with the `event` DataFrame as an argument
result = my_instance.event_day_after_schedule(event)

# Print the result
print(result)
```

## event_day (self, event)
Method for finding all discharge/charge events that appear in the selected period. <br>
Sorted by day.

**Parameters:**

- `self` (self): Dataframe general, period

- `event` (df): DataFrame with all found events

**Returns:**

- `Week day` (int): Number of the day in the week (0 = Monday, ..., 6 = Sunday)

- `month` (int): Month number of the date

- `discharge` (int): 1 in the row if it is a discharge event

- `charge` (int): 1 in the row if it is a charge event

- `charge_day` (int): 1 if there is a charge event in the day

- `discharge_day` (int): 1 if there is a discharge event in the day

- `event` (int): 1 if there is at least one event (charge/discharge) in the day

**Example:**
```py
from KPI import FCR
# Create an instance of your class
my_instance = FCR(database, "2022")

# Assuming you already have the `event` DataFrame from the previous method
# Call the event_day method with the `event` DataFrame as an argument
result = my_instance.event_day(event)

# Print the result
print(result)
```

## energy_event(self)

Method for found all discharge/charge event energy in the select period.

**Parameters:**

- `self` (self): Dataframe general, period

**Returns:**

- `charge_ener` (float - column in df): Energy charge during the period selected in MWh 

- `discharge_ener` (float - column in df): Energy discharge during the period selected in MWh

**Example:**
```py
from KPI import FCR
# Create an instance of your class
my_instance = FCR(database, "2022")

# Call the method
result = my_instance.calculate_event_energy()

# Print the result
print(result)
```
