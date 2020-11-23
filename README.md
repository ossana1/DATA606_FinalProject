# Angela Ossana
# Modeling CO2 Sequestration using the Global Ocean Data Analysis Project (GLODAP)
### UMBC FALL 2020 DATA606 FinalProject
### Dr. Ergun Simsek 
### Project Site 
https://sites.google.com/s/14-zXY-tR-4ddTR09NcwHH0VdedwqjA0Q/p/1mnouXuUqS3ud_088LqPGmpKfiSUgTiD3/edit?ths=true

## The project process map is shown below. The raw CSVs from the GLOPAPv2.2020 repository are cleaned, combined, and NA values are filled using ML random forest regresssion modles. Notebooks and data are saved to this repository for use with Heroku platform as a service to create an interactive user dashboard. The project repository has a second branch (voila-dashboard) to host the necessary files for the Heroku project. 

![Ocean Counts](/images/ProjectMap.png)

## Dashboard 

The dashboard implementation with Heroku is in the __voila-dashboard branch__ of the repository with necessary configuration files. Any commits to this branch are pushed to the Heroku project automatically. <br> https://ossana-angela-data606-final.herokuapp.com/

## Data
The cleaned dataset has been split into CSVs for upload to github repo. They can be loaded into dataframes and merged using the notebook Phase I_Load from Split CSVs. See an image of cruise locations below.  

<p align="center">
  <img width="666" height="334" src="https://github.com/ossana1/DATA606_FinalProject/blob/master/images/OceanRegion.png?raw=true">
</p>

## Notebooks 
### PHASE I
1. Phase I_Exploration and Cleaning Part I <br>
The complete dataset from GLODAP v2.2020 is loaded into a Python dataframe and the columns containing flags for quality control are removed. All rows with negative depth values are also removed. Some exploratory plots are shown, others are changed to markdown cells to prevent making the notebook too large for github upload. <br>

2. Phase I_Cleaning Part II<br>
Columns with mostly null (>90% rows) are removed from the dataset. Figures are made and saved as video/gif. The definitions of the cruise IDs were not clear in the documentation of the dataset. The aim of this notebook was to determine if the cruise IDs repeat the same areas from year to year, and they do not. In addition, those cruise IDs with multiple cruises did not repeat the same locations from year to year. Therefore, the cruise ID should not be used in the ML model as a categorical input variable as the locations are not repeated over the lifetime of the dataset. <br>

3. Phase I_Load from Split CSVs <br>
Example code for merging the split datafiles into a single dataframe for analysis. 

#### Example figure from data exploration of cruises from year to year. 
![Ocean Counts](/images/yearCruises.gif)

### PHASE II
1. Phase II. ML Model Training Part I_ Filling NA Values <br>
The input variables for the CO2 model with NA values in >5% of rows were tested and trained for several ML regression models. The variables were individually tested [gamma, oxygen, apparent O2 utilization, nitrate, silicate, phosphate, total alkilinity, pH] for decision tree, random forest, and linear regression models. The best performing model for each column was saved and applied to each columns' missing values. Random forest regression models were the best performing for all variable columns. An image is shown below demonstrating sparsity of these columns. <br> <br>
![Map](/images/msnolabel.png)<br>

2. Phase II. ML Model Training Part II_ Training CO2 Model<br>
The input variables for the model with NA values have been filled by the previous notebook [gamma, oxygen, apparent O2 utilization, nitrate, silicate, phosphate, total alkilinity, pH]. This notebook trains and applies a random forest regression model to the total CO2 columns of the dataset. No model tuning is performed due to the high performance metrics (R2 ~.99) on test and validation sets. <br> <br>
![Map](/images/MLperformance.png)
<br>

3. Phase II. ML Model Training Part III_DashboardTesting <br>
Testing of Jupyter notebook with Voila for deployment to Heroku platform as a service. Contains data grouping, plotly visuals, and functional testing for user interaction. <br><br>
4. dashboard.ipynb<br>
Under the voila-dashboard project branch, the final cleaned notebook for dashboard use with Heroku. 
<br>

### PHASE III
1. Phase III. GeopandasDivideIntoOceansRegions <br>
This notebook merges rectangular polygons of ocena regions with the latitude and longitude of the cruise locations. The grouped dataset can then be used with FB prophet API in the PhaseIII. FBprophet notebook and other notebooks for visualizations. This notebook was implemented with Google Colabs because of the difficult local geopandas installation.
<br><br>
2. Phase III. FBprophet <br> 
This notebook uses Facebook prophet to predict the future CO2 concentrations. This notebook was used with Google Colabs due to difficulties for local FBprophet installation.
<br><br>
3. Phase III. Figures_DepthPlots <br> 
This notebook tests 3D plotly figures for dashboard implementation and creates conclusion figures. Kmeans clustering was explored. <br><br>
