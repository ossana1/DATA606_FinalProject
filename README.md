# Angela Ossana
# Modeling CO$_2$ Sequestration using the Global Ocean Data Analysis Project (GLODAP)
## UMBC FALL 2020 DATA606 FinalProject
## Dr. Ergun Simsek 
## Project Site 
https://sites.google.com/s/14-zXY-tR-4ddTR09NcwHH0VdedwqjA0Q/p/1mnouXuUqS3ud_088LqPGmpKfiSUgTiD3/edit?ths=true




## Notebooks 
1. Phase I_Exploration and Cleaning Part I
The complete dataset from GLODAP v2.2020 is loaded into a Python dataframe and the columns containing flags for quality control are removed. All rows with negative depth values are also removed. 
2. Phase I_Cleaning Part II
Columns with mostly null (>90% rows) are removed from the dataset. Figures are made and saved as video/gif. The aim of this notebook was to determine if the cruise IDs repeat the same areas from year to year, and they do not. Therefore, the cruise ID should not be used in the ML model as a categorical input variable as the locations are not repeated over the lifetime of the dataset. 

#### Example figure from data exploration of cruises from year to year. 
![Ocean Counts](/images/yearCruises.gif)


#### Example figure from data exploration of cruise IDs. 
![Ocean Counts](/images/cruises.gif)
