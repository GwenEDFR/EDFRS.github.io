# BESS Report Generator

## Dependencies
|Librairies | version|
|-----------|--------|
|FPDF| - |
|datetime| - |
|emoji| - |
|pdf2docx| - |
|os| - |
|tqdm.tqdm| 4.66.2 |

## Summary
Class create PDF report from KPIs plot. Use the .png file store in the ``output/kpi_png/{project}/{year}`` to generate the Report.<br>
The report contain a front page and each page of category available for the selected project.<br/>
**class_name** : PDF

## Methods
### \_\_init\_\_(self, project_name, month_name, plots_folder_path, plots_per_page, first_data_time, last_data_time, sorted_plots=True)

Initializes the object.

**Parameters:**

- `self` (self): Information General

- `project_name` (str): Name of the project chosen

- `month_name` (str): Name of the month for the report

- `plots_folder_path` (str): Path of the folder where the KPIs images are

- `plots_per_page` (int): Number of plots desired per page [1-6]

- `first_data_time` (datetime): Time of the first data of the database. Needs to be in ms

- `last_data_time` (datetime): Time of the last data of the database. Needs to be in ms

- ``list_figure`` (df): List of figures to add in the KPI. Need to have column ['name', 'category', 'object']. Get this list from export_data.get_list_fig 

- ``Confidential`` (bool): Add a confidential text if True (Default: False)

- ``path_to_cache`` (str): Path to cache for generated this report (Optionnal)

**Returns:**

- `Report`: The initialized Report object

### main(self, Report_name:str, Report_path:str, categories)

Main method for creating the report. The content includes:
- First page
- Title for each category
- Image for each category

**Parameters:**

- `self` (self): Information General

- `Report_name` (str): Name of the chosen report

- `Report_path` (str): Path to export the PDF for the output

- `categories` (array): Array with all the names of the categories

**Returns:**

- `Report`: The generated Report object

### category_title(self, title:str)

Method for writing the title of the category.

**Parameters:**

- `self` (self): General information

- `title` (str): Name of the title to print

**Returns:**

- None

### header(self)

This method is responsible for generating the header section of a document.

It includes a custom logo, project name, report date, and other relevant information.

**Args:**

- `self`: The instance of the class.

**Returns:**

- None

### footer(self)

This method is responsible for generating the footer section of a document.

It includes the page numbers.

**Args:**

- `self`: The instance of the class.

**Returns:**

- None

### first_page(self)

This method is responsible for generating the first page of the report.

**Args:**

- `self`: The instance of the class.

**Returns:**

- `first_page` (page): Designed first page of the report

### dimension_KPI(self)

Method for computing the dimension of the KPI plots and the position in the pdf.

**Parameters:**

- `self` (self): General information

**Returns:**

- `fig1_pos_X` (int): Initial position of the image for x

- `fig1_pos_Y` (int): Initial position of the image for y

- `fig_width` (int): Width of the image

- `fig_height` (int): Height of the image

- `gap_x` (int): Gap between image and other component in x

- `gap_y` (int): Gap between image and other component in y

- `comment_space_x` (int): Gap for comment in the pdf

- `gap_comment_x` (int): Ratio for the gap comment

- `gap_ratio_x` (int): Ratio for the gap_x

### add_KPI_plot(self, plots_per_page)

Method for adding KPI plots of the category.

**Parameters:**

- `self` (self): General information

- `plots_per_page` (int): Number of plots per page

**Returns:**

- `KPI_plot_page` (page): Page where the KPI plots are displayed

### create_docx(self, report_pdf_name: str, report_docx_name: str)

Converts a PDF file to a docx file.

**Args:**

- `report_pdf_name` (string): The name of the PDF file to convert.
- `report_docx_name` (string): The name of the docx file to be created.

**Returns:**

- `cv` (docx file): Docx file with the given name in the parameter.

### construct(self, category)

This method is responsible for constructing a list of pages with plots.

It takes into account the specified folder path, number of plots per page, and sorting preference.

**Args:**

- `self`: The instance of the class.
- `Plot_dir` (str): Directory of the graphs to plot.
- `graphs_per_page` (int): Number of plots per page.
- `sorting` (bool): Sorted graphs or not.

**Returns:**

- `List`: A list of pages with plots.