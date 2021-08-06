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

To view the dimensions of the dataframe, we use the shape instance variable of it. (index,column)

![image](https://user-images.githubusercontent.com/81119854/128511552-be4e29ba-1854-499b-9799-88bc5d14051d.png)

Note: The main types stored in pandas objects are float, int, bool, datetime64[ns], datetime64[ns, tz], timedelta[ns], category, and object (string). In addition, these dtypes have item sizes, e.g. int64 and int32.

Let's clean the data set to remove a few unnecessary columns. We can use pandas drop() method as follows:

![image](https://user-images.githubusercontent.com/81119854/128511783-b2894319-0e43-4211-9fc9-3eb0e2d82757.png)

Let's rename the columns so that they make sense. We can use rename() method by passing in a dictionary of old and new names as follows:

![image](https://user-images.githubusercontent.com/81119854/128512126-3f09ac38-e9e0-4234-827e-ea090766f211.png)

We will also add a 'Total' column that sums up the total immigrants by country over the entire period 1980 - 2013, as follows:

![image](https://user-images.githubusercontent.com/81119854/128512252-ed59fdaa-e405-408e-9181-8ea83876ea5d.png)

We can check to see how many null objects we have in the dataset as follows:

![image](https://user-images.githubusercontent.com/81119854/128512322-68f2b9ad-4a09-4318-a85b-82f7283e19dc.png)

Finally, let's view a quick summary of each column in our dataframe using the describe() method.

![image](https://user-images.githubusercontent.com/81119854/128512397-403b703e-d0fe-42b0-882c-699e82a6f8ca.png)

pandas Intermediate: Indexing and Selection (slicing)

Select Column
There are two ways to filter on a column name:

![image](https://user-images.githubusercontent.com/81119854/128520582-a3f2e28e-c6e8-4aa4-a35e-66c507e53bd2.png)

![image](https://user-images.githubusercontent.com/81119854/128520617-de33d836-e552-4218-93ca-11ab5787a751.png)

Example: Let's try filtering on the list of countries ('Country').

![image](https://user-images.githubusercontent.com/81119854/128520951-b9614521-69f5-442d-9fc6-8a7899e1ad42.png)

Let's try filtering on the list of countries ('Country') and the data for years: 1980 - 1985.

![image](https://user-images.githubusercontent.com/81119854/128521039-c6b60b6a-ed5b-4ccf-85e9-a10b59324c7c.png)

Select Row

