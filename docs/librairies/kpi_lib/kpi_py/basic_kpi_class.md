# BASIC KPI class

## **init** (self, database, period)

Initialize the class.<br>
Get the first and last date available in the database.<br>

**Parameters:**

* `self` (self): General information
* `database` (df): The DataFrame representing the database.
* `period` (str): The period information.

**Returns:**

* `None` (None): No return value.

**Example:**

```py
from KPI import BASIC_KPI
# Create a DataFrame representing the database
database = pd.DataFrame({'SOC': [1, 2, 3], '15 min data': [4, 5, 6]})

# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Access the attributes
print("df:", obj.df)
print("period:", obj.period)
```

## SOC (self, soc\_warranty)

Method for compute min, max and mean of the SoC for a certain project in a certain period.\
Use for have the warranty on the SoC too.

**Parameters:**

* `self` (self): Dataframe general, period.
* `soc_warranty` (int): SoC mean constraint by the warranty.

**Returns:**

* `soc_min` (int - column in df): DataFrame of the minimum SoC for a certain period.
* `soc_max` (int - column in df): DataFrame of the maximum SoC for a certain period.
* `soc_mean` (int - column in df): DataFrame of the average SoC for a certain period.
* `soc_cumulative` (int - column in df): DataFrame of the cumulative average SoC for a certain period.
* `soc_warranty_month` (int - column in df): Warranty SoC per month for this specific project.

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the SOC method with the soc_warranty value
soc_results = obj.SOC(soc_warranty=80)

# Print the SOC results
print(soc_results)
```

## SOC\_sorted (self)

Method for compute min, max and mean of the SoC sorted by period for a certain project in a certain period.

**Parameters:**

* `self` (self): Dataframe general, period.

**Returns:**

* `soc_min_HLZ` (int - column in df): DataFrame of the minimum SoC for a certain period. With HLZ = 'FCR', 'on peak', 'off peak'.
* `soc_max_HLZ` (int - column in df): DataFrame of the maximum SoC for a certain period. With HLZ = 'FCR', 'on peak', 'off peak'.
* `soc_mean_HLZ` (int - column in df): DataFrame of the average SoC for a certain period. With HLZ = 'FCR', 'on peak', 'off peak'.
* `month` (int - column in df): Month number for the data in the df.

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the SOC_sorted method
soc_sorted_results = obj.SOC_sorted()

# Print the SOC sorted results
print(soc_sorted_results)
```

## energy (self, ener\_dis\_warranty)

Compute energy consumed, delivered and lost per month. The values stored are the cumulative energy at POC.\
Value in MWh.

**Parameters:**

* `self` (self): Dataframe general, period.
* `ener_dis_target` (int): Energy discharge target by the warranty contract.
* `ener_dis_max` (int): Energy discharge max authorize by the warranty without losing the warranty. 

**Returns:**

* `consumed` (float - column in df): Energy consumed during the selected period at POC in MWh.
* `delivered` (float - column in df): Energy delivered during the selected period at POC in MWh.
* `losses` (float - column in df): Energy losses by the system (consumed - delivered) in MWh.
* `losses_%` (float - column in df): Percentage of energy loss by the system.
* `ener_cumul` (float - column in df): Energy delivered cumulative at POC in MWh.
* `ener_target` (float - column in df): Energy per month target by the warrranty of the selected project.
* `ener_max` (float - column in df): Energy per month max authorized by the warrranty of the selected project.
* `difference_target` (float - column in df): Difference of energy between ener\_cumul and ener\_target in MWh.
* `difference_max` (float - column in df): Difference of energy between ener\_cumul and ener\_max in MWh.

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the energy method with the ener_dis_warranty value
energy_results = obj.energy(ener_dis_target=100, ener_dis_max=300)

# Print the energy results
print(energy_results)
```

## energy\_sorted (self)

Compute energy consumed, delivered per month sorted by type of period (on peak, off peak, FCR).<br>
The values stored are the cumulative energy at POC and are returned in MWh.

**Parameters:**

* `self` (self): Dataframe general, period.

**Returns:**

* `consumed_FCR` (float - column in df): Energy consumed during the FCR period at POC in MWh.
* `consumed_on peak` (float - column in df): Energy consumed during the on peak period at POC in MWh.
* `consumed_off peak` (float - column in df): Energy consumed during the off peak period at POC in MWh.
* `delivered_FCR` (float - column in df): Energy delivered during the FCR period at POC in MWh.
* `delivered_on peak` (float - column in df): Energy delivered during the on peak period at POC in MWh.
* `delivered_off peak` (float - column in df): Energy delivered during the off peak period at POC in MWh.

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the energy_sorted method
energy_sorted_results = obj.energy_sorted()

# Print the energy sorted results
print(energy_sorted_results)
```

## number\_cycle (self, energy\_eol)

Calculate the number of cycles done per month. Cycle Compute with EOL value like : = Energy discharged in a month/EOL.

**Parameter:**

* `self` (self): Dataframe general, period.
* `energy_eol` (int): Energy at end of life (EOL) for calculation.

**Return:**

* `cycle_num` (int - column in df): Number of cycles with EOL.

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the number_cycle method with the energy_eol value
cycle_results = obj.number_cycle(energy_eol=1000)

# Print the number of cycles
print(cycle_results)
```

## availability (self)

Method for computing the availability for a certain project in a certain period.

**Parameter:**

* `self` (self): Dataframe general, period.

**Returns:**

* `availability` (int - column in df): DataFrame of the average availability for a certain period.

**Example:**

```python
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the availability method
availability_results = obj.availability()

# Access the availability column in the results
availability_column = availability_results['availability']

# Print the availability column
print(availability_column)
```

## number\_peak\_miss (self)

Save in a dataFrame the date of missed peak. Theorically this dataFrame will be empty, no peak missed in normal mode.

**Parameter:**

* `self` (self): Dataframe general, period.

**Returns:**

* `Date` (datetime - column in df): Date of the selected row.
* `15 min data` (float - column in df): Power from last 15 minutes in kW.
* `permissible power` (float - column in df): Power maximal to not exceed during peak shave in kW.
* `power_misses` (float - column in df): Amount of power more than the permissible power.

**Example:**

```python
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the number_peak_miss method
peak_miss_results = obj.number_peak_miss()

# Access the columns in the results
date_column = peak_miss_results['Date']
data_column = peak_miss_results['15 min data']
permissible_power_column = peak_miss_results['permissible power']
power_misses_column = peak_miss_results['power_misses']

# Print the columns
print("Date:", date_column)
print("15 min data:", data_column)
print("Permissible power:", permissible_power_column)
print("Power misses:", power_misses_column)
```

## peak\_success(self, project:str)

Save in a table all the peak shave. Definition of a peak shave is :&#x20;

* All peak when the battery is on 'on peak' period that imply a discharge of the batterie
* if several peak shave within 15 min from the riseing edge of the first peak is count as 1 peak (see graph below)&#x20;
* All peak higher than 2% of the nominal energy (nominal power \* 1 hour)&#x20;

<img src="../../../.gitbook/assets/file.excalidraw (2).svg" alt="Graphical explanation of the computation of the count of peak shaving" class="gitbook-drawing">

**Parameter:**

* `self` (self): Dataframe general, period.
* `project` (str): Name of the project selected.

**Returns:**

* `Date`(datetime - column in df): Date of the selected peak.
* `ener_peak`(float - column in df): Energy used to shave the peak \[kWh].
* `month`(int - column in df): Month of the date.&#x20;

```python
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the number_peak_miss method
peak_shave = obj.peak_sucess("HYHA")

# Access the columns in the results
date_column = peak_shave ['Date']
ener_column = peak_shave ['ener_peak']
month_column = peak_shave ['month']

# Print the columns
print("Date:", date_column)
print("Energy:", ener_column)
print("month:", month_column)
```

## analyse\_load\_curve\_dso (self)

Method for computing min, max, and mean of the load for a certain project in a certain period.<br>The 15 min data are for the past 15 minutes not the next 15 minutes. 

**Parameter:**

* `self` (self): Dataframe general, period.

**Returns:**

* `load_curve` (df): DataFrame of the load for a certain period.
* `load_curve_mean` (df): DataFrame of the average load for a certain period in kW.
* `load_curve_min` (df): DataFrame of the minimum load for a certain period in kW.
* `load_curve_max` (df): DataFrame of the maximum load for a certain period in kW.

**Example:**

```python
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the analyse_load_curve_dso method
load_curve, load_curve_mean, load_curve_min, load_curve_max = obj.analyse_load_curve_dso()

# Print the load curves
print("Load Curve:")
print(load_curve)

print("Load Curve Mean:")
print(load_curve_mean)

print("Load Curve Min:")
print(load_curve_min)

print("Load Curve Max:")
print(load_curve_max)
```

## analyse\_load\_max (self, to\_atypic=10)

Method for computing the maximum peak in on/off peak of the load for a certain project in a certain period. Computes if atypical or not.

**Parameters:**

* `self` (self): Dataframe general, period.
* `to_atypic` (int)(default 10): Percentage of delta to reach for being atypical for a certain project. Information can be found in the parameters project file.

**Returns:**

* `pmax_off/on_peak` (float - columns in df): Value maximum found in the month (off peak is all period except on peak).
* `date_pmax_off/on_peak` (datetime - columns in df): Date where the maximum peak appears in kW.
* `delta` (float - columns in df): In percent, the difference between both on/off peak.
* `atypical` (str - columns in df): If status atypical is reached (delta > %).

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the analyse_load_max method
load_max_results = obj.analyse_load_max(to_atypic=20)

# Print the load max results
print(load_max_results)
```

## auxiliaries\_consumption (self)

Method for calculation of auxiliary consumption.

**Parameters:**

* `self` (self): Dataframe general, period

**Returns:**

* `aux_min_N` (float - columns in df ): DataFrame of all minimum value from aux 1, 2, 3 (=N) for the period given
* `aux_max_N` (float - columns in df ): DataFrame of all maximum value from aux 1, 2, 3 (=N) for the period given
* `aux_mean_N` (float - columns in df ): DataFrame of all average value from aux 1, 2, 3 (=N) for the period given
* `aux_min_tot` (float - columns in df ): DataFrame of total minimum value from aux 1, 2, 3 for the period given
* `aux_max_tot` (float - columns in df ): DataFrame of total maximum value from aux 1, 2, 3 for the period given
* `aux_mean_tot` (float - columns in df ): DataFrame of total average value from aux 1, 2, 3 for the period given

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the auxiliaries consumption 
aux_cons = obj.auxiliaries_consumption()

# Print auxiliaries consumption 
print(aux_cons)
```

## aux\_energy (self)

Compute energy consumed from auxiliaries per month.

**Parameter:**

* `self` (self): Dataframe general, period

**Returns:**

* `ener_aux_N` (float): Value of auxiliaries 1, 2, 3 (=N) energy for the selected period. Values are in kWh
* `ener_auxs` (float): Value of the total energy from auxiliaries 1, 2, 3. Values are in kWh

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
obj = BASIC_KPI(database, 'month')

# Call the aux_energy method
result = obj.aux_energy()

# Print the result
print(result)
```

## summary (self, project, year)

Method for compare summary of KPIs from previous year.

**Parameters:**

* `self` (self): Dataframe general, period
* `project` (str): Name of the selected project
* `year` (str): Year of the selected project

**Returns:**

* `KPI` (str - column in df): KPIs name summarized
* `Actual year` (values - column in df): Value of KPIs for the selected year
* `Years-N` (values - column in df): Value of KPIs for years-N of the selected year Information of available years in the parameters\_project excel file
* `warranty` (values - column in df): Values where warranty is stored (if needed) otherwise copy of the 2024 column
* `group` (int - column in df): Group number to sorted in the table

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
my_instance = BASIC_KPI(database, 'month')

# Call the summary method with the appropriate arguments
result = my_instance.summary("MyProject", "2022")

# Print the result
print(result)
```

## period\_time (self, month\_short)

Compute overview of hours per period within the selected month.

**Parameters:**

* `self` (self): Dataframe general, period
* `month_short` (str): Number of the month selected

**Returns:**

* `periods` (df): Dataframe with all information (percentage, hours) of period for the month selected

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
my_instance = BASIC_KPI(database, 'month')

# Call the method with the appropriate arguments
result = my_instance.period_time("04")

# Print the result
print(result)
```

## period\_time\_overview (self, year, project)

Compute prediction data with real to get the number of hours per periods for an entire year.

**Parameters:**

* `self` (self): Dataframe general, period
* `year` (str): Year selected for the overview
* `project` (str): Name of the project

**Returns:**

* `period_time` (df): Dataframe with all information (percentage, hours, month, predict, count) of period for the year selected

**Example:**

```py
from KPI import BASIC_KPI
# Create an instance of the class
my_instance = BASIC_KPI(database, 'month')

# Call the method with the appropriate arguments
result = my_instance.period_time_overview("2024", "Myproject")

# Print the result
print(result)
```
