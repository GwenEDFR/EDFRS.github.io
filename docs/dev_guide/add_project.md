# How to add a project in your report
1) In the folder ``Data/data_project``, create a folder with the short name of the new project (ex: WERN for Wernigerode). This name will be use everywhere in the code. <br>
2) Create the folder on the data year and save your csv data files in.<br>
3) In ``Libraries/KPI_library/HLZ.py``, copy a project class, change the name clas with the name of the new project. Keep only the methods with the available year for this project, and change the time of on peak and FCR.<br>
4) In ``Data/data_project/name_of_new_project`` paste the parameter_project.xlsx and enter the information about this project. Rename this file parameters_name_new_project.xlsx.<br>
5) In ``Libraries/KPI_library/parameters_projects.py`` create a new class with the name of your project and write the same than the others project by changing the path of the file.<br>
6) In ``Data/data_appendix/`` add a new background with the name 'Background_first_page_report_' + name of the new project (ex: Background_first_page_report_WERN.png)<br>
7) You're finish to add a new project, enjoy your report for this new one !<br>

> ⚠️ **Format**: Data Format need to be the same than the other project (see [Data format](../user_guide/Data.md)).


> 💡 **Tips**: If you have some doubt about the architecture, navigate on the other project folder. 