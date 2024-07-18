# KPI plot

## Dependencies

| Librairies                     | version |
| ------------------------------ | ------- |
| parameters\_project.py (local) | -       |
| KPI.py (local)                 | -       |
| pandas                         | 2.2.1   |
| plotly.graph\_objects          | 5.20.0  |
| plotly.subplots                | 5.20.0  |

## Summary

Class create plots from KPIs.py. Use the KPI.py library to generate the data. Normal size of an image 1200x800 px.\
**class\_name** : plot\_KPI

## General variable
| Color         | Hex Code   | Color Sample  |
| ------------- | ---------- | ------------- |
| DARK_BLUE     | '#001A70'  | <span style="color: #001A70; font-size: 20px; display: flex; justify-content: center;">■</span> |
| MEDIUM_BLUE   | '#1057C8'  | <span style="color: #1057C8; font-size: 20px; display: flex; justify-content: center;">■</span> |
| LIGHT_BLUE    | '#1089FF'  | <span style="color: #1089FF; font-size: 20px; display: flex; justify-content: center;">■</span> |
| MEDIUM_GREY   | '#666666'  | <span style="color: #666666; font-size: 20px; display: flex; justify-content: center;">■</span> |
| LIGHT_GREY    | '#E0E0E0'  | <span style="color: #E0E0E0; font-size: 20px; display: flex; justify-content: center;">■</span> |
| DARK_GREEN    | '#4F9E30'  | <span style="color: #4F9E30; font-size: 20px; display: flex; justify-content: center;">■</span> |
| MEDIUM_GREEN  | '#88D910'  | <span style="color: #88D910; font-size: 20px; display: flex; justify-content: center;">■</span> |
| LIGHT_GREEN   | '#C0E410'  | <span style="color: #C0E410; font-size: 20px; display: flex; justify-content: center;">■</span> |
| DARK_ORANGE   | '#FE5716'  | <span style="color: #FE5716; font-size: 20px; display: flex; justify-content: center;">■</span> |
| MEDIUM_ORANGE | '#FF861D'  | <span style="color: #FF861D; font-size: 20px; display: flex; justify-content: center;">■</span> |
| LIGHT_ORANGE  | '#FFB210'  | <span style="color: #FFB210; font-size: 20px; display: flex; justify-content: center;">■</span> |
| BLACK         | '#000000'  | <span style="color: #000000; font-size: 20px; display: flex; justify-content: center;">■</span> |
| DARK_GREY     | '#333333'  | <span style="color: #333333; font-size: 20px; display: flex; justify-content: center;">■</span> |
| TOTAL         | '#2E603F'  | <span style="color: #2E603F; font-size: 20px; display: flex; justify-content: center;">■</span> |
| WARRANTY      | '#813640'  | <span style="color: #813640; font-size: 20px; display: flex; justify-content: center;">■</span> |

**TITLE_FONT_SIZE** = 25
**TICK_FONT_SIZE** = 20
**AXIS_FONT_SIZE** = 23
**TEXT_FONT_SIZE** = 20
**LEGEND_FONT_SIZE** = 20
**LEGEND_FONT_SIZE_S** = 15

## General methods
### hex_opacity(hex_color, opacity)

Transforms a color with the selected opacity.

**Parameters:**

- `hex_color` (str): The hexadecimal color code (e.g., "#RRGGBB").
- `opacity` (float): The opacity value between 0 and 1, where 0 represents the normal color and 1 represents full transparency.

**Returns:**

- `new_hex_color` (str): The new hexadecimal color code with the specified opacity.

**Example:**
```python
# Call the hex_opacity function
result = hex_opacity("#001A70", 0.5)

# Print the new hexadecimal color code with opacity
print(result)
```
| Hex Code   | Result  |
| ---------- | ------------- |
| <span style="color: #001A70; font-size: 20px; display: flex; justify-content: center;">■</span>  | <span style="color: #7f8cb7; font-size: 20px; display: flex; justify-content: center;">■</span> |

### check_color(color)

Check if the color selected is available, otherwise raise an error. Verification for each methods in the class plot_KPI. 

**Parameters:**

- `color` (str): The str color entered.

**Returns:**

- ``KeyError`` (error): If str color is not ['blue' or 'orange' or 'green'].

**Example:**
```python
import KPI_plot 
# Call the color_check function
KPI_plot.check_color('blue')
>> pass
# Call the color_check function
KPI_plot.check_color('Blue')
>> KeyError (Invalid color, please select color available : 'blue', 'orange', 'green')
```

## Class plot_KPI

### **init**(self, database, project, year) -> None

Initialize the import\_data class.

**Parameters:**

* `self` (self): General information
* `database` (df): Database used for calculation of the KPIs
* `project` (str): The project name.
* `year` (str): The year of the project.

**Returns:**

* `None` (None): No return value.

**Example:**

```python
# Create an instance of the class
obj = plot_KPI(database=database, project="HYHA", year="2024")

# Access the attributes
print("project:", obj.project)
print("year:", obj.year)
print("year_short:", obj.year_short)
```

### analyze\_load\_plot(self, color='blue')

Module for plot the load curve for a certain project in a certain period.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_analyze_load` (go.Figure): Figure containing the plot of the load curve

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').analyze_load_plot().show()
# return :
```

![fig\_analyze\_load HYHA April 2024](../../image/KPI\_plot\_example/24\_2\_context\_analyze\_load\_HYHA.png)

### aux\_plot(self, color='blue')

Module for plot the auxiliaries consumption graph for a certain project in a certain period.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_aux_cons` (go.Figure): Figure contain plot of the auxiliaries consumption

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').aux_plot().show()
# return :
```

![fig\_aux\_plot HYHA April 2024](../../image/KPI\_plot\_example/24\_3\_op\_sumup\_aux\_plot\_HYHA.png)

### aux\_content(self, color='blue')

Module for table the auxiliaries content for a certain project.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_aux_content` (go.Figure): Figure contain content on each aux\_N

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').fig_aux_content().show()
# return :
```

![fig\_aux\_content HYHA April 2024](../../image/KPI\_plot\_example/24\_3\_op\_sumup\_aux\_content\_HYHA.png)

### aux\_energy(self, color='blue')

Module for plot energy from the auxiliaries for a certain project.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_ener_aux` (go.Figure): Figure contain bar of energy per month

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').aux_energy().show()
# return :
```

![fig\_ener\_aux HYHA April 2024](../../image/KPI\_plot\_example/24\_3\_op\_sumup\_aux\_energy\_HYHA.png)

### peak\_miss\_table(self, color='blue')

Module for plot the table of missed peak for a certain project in a certain period.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_peak_miss` (go.Figure): Figure contain table of the peak missed. Normally empty.

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').peak_miss_table().show()
# return :
```

![fig\_peak\_miss HYHA April 2024](../../image/KPI\_plot\_example/24\_3\_op\_sumup\_peak\_miss\_HYHA.png)

### soc\_plot(self, color='blue')

Module for plot the graph of average and cumulative SoC for a certain project in a certain period.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_soc` (go.Figure): Figure contain graph of the SOC

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').soc_plot().show()
# return :
```

![fig\_soc HYHA April 2024](../../image/KPI\_plot\_example/24\_4\_warranty\_soc\_plot\_HYHA.png)

### soc\_sorted\_plot(self, color='blue')

Module for plot the graph of average, min and max SoC for a certain project for each HLZ period in a month.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_soc_sorted` (go.Figure): Figure contain graph of the SOC sorted by type HLZ ('on peak', 'off peak', 'FCR')

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').soc_sorted_plot().show()
# return :
```

![fig\_soc\_sorted HYHA April 2024](../../image/KPI\_plot\_example/24\_4\_warranty\_soc\_sorted\_HYHA.png)

### energy\_warranty\_plot(self, color='blue')

Module for plot the compared value of cumulative energy and warranty cumulative energy.\


**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_energy_warranty_poc_month` (go.Figure): Figure contain graph of the energy at POC + cumulative energy compared to warranty energy

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').energy_warranty_plot().show()
# return :
```

![figure 24\_2\_Warranty\_energy\_warranty\_HYHA](../../image/KPI\_plot\_example/24\_2\_Warranty\_b\_energy\_warranty\_HYHA.png)

### energy\_poc\_plot(self, color='blue')

Module for plot the graph of energy at POC for a certain project in a certain period.\


**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_energy_poc_month` (go.Figure): Figure contain graph of the energy at POC + cumulative energy compared to warranty energy

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').energy_poc_plot().show()
# return :
```

![fig\_energy\_poc\_month HYHA April 2024](../../image/KPI\_plot\_example/24\_3\_Operation\_e\_energy\_poc\_HYHA.png)

### energy\_sorted\_plot(self, color='blue')

Module for plot the graph of energy at POC sorted by period for a certain project in a certain period.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_energy_poc_month_sorted` (go.Figure): Figure contain graph of the energy at POC for each period

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').energy_sorted_plot().show()
# return :
```

![fig\_energy\_poc\_month\_sorted HYHA April 2024](../../image/KPI\_plot\_example/24\_3\_op\_sumup\_energy\_sorted\_HYHA.png)

### number\_cycle\_plot(self, color='blue')

Module for plot the graph of number of cycle for a certain project in a certain period.\
Cycle Compute with EOL value like : = Energy discharged in a month/EOL.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_number_cycle` (go.Figure): Figure contain graph of the number of cycle per period

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').number_cycle_plot().show()
# return :
```

![fig\_number\_cycle HYHA April 2024](../../image/KPI\_plot\_example/24\_4\_warranty\_number\_cycle\_HYHA.png)

### availability\_plot(self, color='blue')

Module for plot the graph of percentage of availability for a certain project in a certain period.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_availability` (go.Figure): Figure contain graph of the percentage of availability

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').availability_plot().show()
# return :
```

![fig\_availability HYHA April 2024](../../image/KPI\_plot\_example/24\_3\_op\_sumup\_availability\_HYHA.png)

### summary\_KPI\_past\_year\_table(self, color='blue')

Module for plot the table of summarized KPI from the previous years for a certain project.\
Data used are stored in excel parameters of the specific project, don't touch here to change it.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_summary` (go.Figure): Figure contain table of the KPI summarized

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').summary_KPI_past_year_table().show()
# return :
```

![fig\_summary HYHA April 2024](../../image/KPI\_plot\_example/24\_1\_overview\_summary\_HYHA.png)

### overview\_table(self, color='blue')

Module for plot the table of Overview KPIs and warranty for a certain project.\
Data used are stored in excel parameters of the specific project, don't touch here to change it.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_overview` (go.Figure): Figure contain table of the overviewed KPIs

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').overview_table().show()
# return :
```

![fig\_overview HYHA April 2024](../../image/KPI\_plot\_example/24\_1\_overview\_overview\_HYHA.png)

### load\_max\_plot(self, color='blue')

Module for plot the table of Pmax on/off peak for a certain project.\
Useful to know if project atipycal or not.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_load_max` (go.Figure): Figure contain table of the Pmax on/off peak + atipycal values

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').load_max_plot().show()
# return :
```

![fig\_load\_max HYHA April 2024](../../image/KPI\_plot\_example/24\_2\_context\_load\_max\_HYHA.png)

### event\_day(self, color='blue')

**FCR method**\
Module for plot the event days and event days after schedule for a certain project.\
Useful to know how many day after schedule we do. Warranty to respect.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_event_day` (go.Figure): Figure contain plot of event day per month

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').event_day().show()
# return :
```

![fig\_event\_day HYHA April 2024](../../image/KPI\_plot\_example/24\_5\_FCR\_event\_day\_HYHA.png)

### event\_count(self, color='blue')

**FCR method**\
Module for plot the number of event charge and discharge for a certain project.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_event` (go.Figure): Figure contain plot of number event charge/discharge per month

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').event_count().show()
# return :
```

![fig\_event HYHA April 2024](../../image/KPI\_plot\_example/24\_5\_FCR\_event\_count\_HYHA.png)

### event\_energy(self, color='blue')

**FCR method**\
Module for plot the energy from a charge or discharge event for a certain project.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_ener_event` (go.Figure): Figure contain plot of energy charge and discharge event per month in MWh

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').event_energy().show()
# return :
```

![fig\_ener\_event HYHA April 2024](../../image/KPI\_plot\_example/24\_5\_FCR\_event\_energy\_HYHA.png)

### period\_time\_pie\_chart(self, color='blue')

Module for plot the pie chart of hours for periods in the selected month.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_period` (go.Figure): Figure pie chart percentage of period for this month

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').period_time_pie_chart().show()
# return :
```

![fig\_period HYHA April 2024](../../image/KPI\_plot\_example/24\_3\_Operation\_g\_period\_time\_HYHA.png)

### period\_overview\_plot(self, color='blue')

Module for plot overview of hours for periods in the selected year.

**Parameter:**

* `self` (self): General information

* `color` (str): General color of the plot. Available ['blue', 'orange', 'green']

**Return:**

* `fig_period_overview` (go.Figure): Figure of the period percentage for this year per month

**Example:**

```python
plot_KPI(database, 'HYHA', '2024').period_overview_plot().show()
# return :
```

![fig\_period\_overview HYHA April 2024](../../image/KPI\_plot\_example/24\_1\_Overview\_c\_period\_overview\_HYHA.png)
