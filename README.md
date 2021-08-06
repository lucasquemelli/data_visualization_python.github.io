# data_visualization_python.github.io
This is a repository about data visualization using python libraries.

# Introduction to Matplotlib and Line Plots

The aim of these labs is to introduce data visualization with Python as concrete and as consistent as possible.

The majority of the plots and visualizations will be generated using data stored in pandas dataframes. Therefore, in this lab, we provide a brief crash course on pandas. 

Exploring Datasets with pandas

Pandas is an essential data analysis toolkit for Python. Pandas is a Python package providing fast, flexible, and expressive data structures designed to make working with “relational” or “labeled” data both easy and intuitive. 

The Dataset: Immigration to Canada from 1980 to 2013

Dataset Source: International migration flows to and from selected countries - The 2015 revision.

The dataset contains annual data on the flows of international immigrants as recorded by the countries of destination. The data presents both inflows and outflows according to the place of birth, citizenship or place of previous / next residence both for foreigners and nationals.

The first thing we'll do is import two key data analysis modules: pandas and numpy.

![image](https://user-images.githubusercontent.com/81119854/128508140-9bf896bb-4a00-4ff2-9e3a-730a36a66306.png)

Let's download and import our primary Canadian Immigration dataset using pandas's read_excel() method.

Normally, before we can do that, we would need to download a module which pandas requires reading in Excel files. This module was openpyxl (formerlly xlrd). For this lab, the course maker have pre-installed this module. Otherwise, we would need to run the following line of code to install the openpyxl module: ! pip3 install openpyxl

![image](https://user-images.githubusercontent.com/81119854/128508511-8da7029c-df60-4348-bd69-1dbdedf05e09.png)

Let's view the top 5 rows of the dataset using the head() function.

![image](https://user-images.githubusercontent.com/81119854/128508601-d7f1499d-d409-4b70-9ef0-d1ccb5c292e1.png)

We can also view the bottom 5 rows of the dataset using the tail() function.

![image](https://user-images.githubusercontent.com/81119854/128508679-81bf3ae9-b3e0-4ef9-93cf-5ef1d29e4f90.png)

When analyzing a dataset, it's always a good idea to start by getting basic information about your dataframe. We can do this by using the info() method.

![image](https://user-images.githubusercontent.com/81119854/128508819-abaa62ff-7c41-41d9-8c67-9c4dcae6a1ad.png)

To get the list of column headers we can call upon the data frame's columns instance variable.

![image](https://user-images.githubusercontent.com/81119854/128509011-aa4c4b04-d819-473c-948b-afff49b5a98b.png)

Similarly, to get the list of indices we use the .index instance variables.

![image](https://user-images.githubusercontent.com/81119854/128509102-bcce551a-da10-4239-9bc4-7c488d3b205c.png)

Note: The default type of intance variables index and columns are NOT list.

![image](https://user-images.githubusercontent.com/81119854/128509204-99a4197b-2982-41e7-a4e7-d5eace87303f.png)

To get the index and columns as lists, we can use the tolist() method.

![image](https://user-images.githubusercontent.com/81119854/128509357-c621f3d8-f9fd-4a94-a2a2-a3c8f08166ad.png)

![image](https://user-images.githubusercontent.com/81119854/128509396-6bf12d93-2873-4b27-bd80-3cb12d0817ac.png)

![image](https://user-images.githubusercontent.com/81119854/128509448-c95b868b-40ec-4196-a0b8-39ad19a2008f.png)
