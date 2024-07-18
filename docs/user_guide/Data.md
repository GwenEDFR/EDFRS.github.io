# Data How it's work ?

You can see this system like a box with input, output and some buttons.&#x20;
![Representation of this code like a box](../image/draw/file.excalidraw%20(1).png)

You can have many ressources as long as the file of input is in csv format and have a time in this file.


| Project support | Grafana                         | SmartBlue                       | LMS                             |
| --------------- | ------------------------------- | ------------------------------- | ------------------------------- |
| HYHA            | ![](../icon/material/check.png) | ![](../icon/material/cross.png) | ![](../icon/material/cross.png) |
| BREM            | ![](../icon/material/check.png) | ![](../icon/material/cross.png) | ![](../icon/material/check.png) |
| WERN            | ![](../icon/material/check.png) | ![](../icon/material/cross.png) | ![](../icon/material/cross.png) |
| TANN            | ![](../icon/material/cross.png) | ![](../icon/material/check.png) | ![](../icon/material/check.png) |

## Required tag

Those tags are needed to get the KPI monthly report (Normaly if you download all the panel from Grafana/Export you have all the tags available).


| Tag name                | Data type   |
| ----------------------- | ----------- |
| 'Time'                  | `Timestamp` |
| 'aux 1'                 | `float`     |
| 'aux 2'                 | `float`     |
| 'aux 3'                 | `float`     |
| 'availability'          | `int`       |
| '15 min data'           | `float`     |
| '15 average power'      | `float`     |
| 'permissible power'     | `float`     |
| '\[L]'                  | `float`     |
| '\[AP2]'                | `float`     |
| 'BESS power'            | `float`     |
| 'P'                     | `float`     |
| 'SOC'                   | `float`     |
| 'LMS request discharge' | `float`     |
| 'consumed'              | `float`     |
| 'delivred'              | `float`     |

## Tutorial for getting data from Grafana

1. Go one the website and open the export dashboard.\
   ![Grafana go on export dashboard](../image/Grafana\_export\_tuto/export\_dashboard.png)
2. Select the project you want and the time range.\

3. For each panel. Go on the 3 dot (left top of the panel). Select Inspect>Data.\
   ![Select inspect>data in the exportation process](../image/Grafana\_export\_tuto/Inspect\_data.png)
4. Now select in the Show data frame : Series joined by time. Untick Formatted data (otherwise the time format in not support by this code) and click on the button "Download CSV".\
   ![Download CSV from grafana](../image/Grafana\_export\_tuto/download\_csv.png)
5. Final step is to save this files in the good place. Copy the download files in `Data>Data_project>{name of the project}>{year of this data}`.\
   I continue with the example, we have download data from the HYHA project in 2024, so I'll saved the data in `Data>Data_project>HYHA>2024`\

6. You are able to use the data from Grafana in the report !
