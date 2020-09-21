# Angela Ossana
# Modeling CO2 Sequestration using the Global Ocean Data Analysis Project (GLODAP)
## UMBC FALL 2020 DATA606 FinalProject
## Dr. Ergun Simsek 
## Project Site 
https://sites.google.com/s/14-zXY-tR-4ddTR09NcwHH0VdedwqjA0Q/p/1mnouXuUqS3ud_088LqPGmpKfiSUgTiD3/edit?ths=true

## Data
The cleaned dataset has been split into CSVs for upload to github repo. They can be loaded into dataframes and merged using pd.concat. 



## Notebooks 
### PHASE I
1. Phase I_Exploration and Cleaning Part I <br>
The complete dataset from GLODAP v2.2020 is loaded into a Python dataframe and the columns containing flags for quality control are removed. All rows with negative depth values are also removed. <br>
2. Phase I_Cleaning Part II<br>
Columns with mostly null (>90% rows) are removed from the dataset. Figures are made and saved as video/gif. The definitions of the cruise IDs were not clear in the documentation of the dataset. The aim of this notebook was to determine if the cruise IDs repeat the same areas from year to year, and they do not. In addition, those cruise IDs with multiple cruises did not repeat the same locations from year to year. Therefore, the cruise ID should not be used in the ML model as a categorical input variable as the locations are not repeated over the lifetime of the dataset. 

#### Example figure from data exploration of cruises from year to year. 
![Ocean Counts](/images/yearCruises.gif)

