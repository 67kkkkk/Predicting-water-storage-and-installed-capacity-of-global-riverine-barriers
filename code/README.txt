#  Predicting water storage and installed capacity of global riverine barriers
Using a trained model to predict the attributes of obstacles with only geographic coordinates
Modified 6/4/2024
Version 1.0

================================================
*** Citation ***

Please cite the following publications:

##########
##########


###    data source：
Environmental data Source:
http://thredds.northwestknowledge.net:8080/thredds/catalog/TERRACLIMATE_ALL/data/catalog.html
river net Data Source:
https://www.hydrosheds.org/products/hydrobasins


1) download environmental data

visit ( http://thredds.northwestknowledge.net:8080/thredds/catalog/TERRACLIMATE_ALL/data/catalog.html )   and download the environmental data
Please download the nc file provided by HTTPServer
The URL of the aet file is as follows:
http://thredds.northwestknowledge.net:8080/thredds/catalog/TERRACLIMATE_ALL/data/catalog.html?dataset=TERRACLIMATE_ALL_SCAN/data/TerraClimate_aet_2022.nc

Please download the following environment using similar methods data files, using the variable name {PDSI, pet, PPT, q, soil, tmin, tmax} instead of aet in turn is part of the can
Example:
  TerraClimate_aet_2022.nc   
  TerraClimate_PDSI_2022.nc 


######################
######################
Store the 8 nc files downloaded above in the uncompressed folder  -./python/data/nc:


2) River network data
River network data has been preprocessed and downloaded with the compressed package, no processing is required


3）barrier data
Please provide barrier data according to actual requirements, we have provided two smaller data cases excample.csv file
In addition, please use the obstacle data box of CSV format file instead of SHP at run time, mainly for easier review, because data that is not easily captured on the river network may be lost during execution


###  actual operation

3) data preprocessing
python section: Please under the arcpy module of python version 2.7 of pycharm

##########  step1 ########################
Run the 00_nc2tif.py function in the python folder
The main function of this function is to decompose nc files into tif files
There are 480 items in the Tiff file after running
#####
########################################

########## step2 #########################
Run the 01_damdata.py function in the python folder
The main function of this function is to extract the environment data for the corresponding position of obstacles
After running, the corresponding data will be generated under "python\data\damdata". You can move the data to the R file from the last two lines of the python file, or you can move the data to the -./R/data/damdata folder yourself
#####
########################################

R section： please download the 3.40.0.1 version of h2o package      #   h2o version： 3.40.0.1       #   https://cran.r-project.org/src/contrib/Archive/h2o/

Run the predicted.r function to complete the prediction. The prediction result will be displayed in the -./R/data folder