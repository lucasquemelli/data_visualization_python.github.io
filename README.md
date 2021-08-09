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

There are main 2 ways to select rows:

![image](https://user-images.githubusercontent.com/81119854/128521144-948d7cf2-5b38-4ab8-a8a3-6882f108cb3a.png)

Before we proceed, notice that the default index of the dataset is a numeric range from 0 to 194. This makes it very difficult to do a query by a specific country. For example to search for data on Japan, we need to know the corresponding index value.

This can be fixed very easily by setting the 'Country' column as the index using set_index() method.

![image](https://user-images.githubusercontent.com/81119854/128521413-dda9d28a-751d-4337-8c8d-3fa793f17bbf.png)

![image](https://user-images.githubusercontent.com/81119854/128521485-a3361042-96a1-474c-8971-0a9ec7b8c6e3.png)

Example: Let's view the number of immigrants from Japan (row 87) for the following scenarios: 1. The full row data (all columns) 2. For year 2013 3. For years 1980 to 1985

![image](https://user-images.githubusercontent.com/81119854/128521841-6b84df65-f06f-4379-b47d-f89a78f8b48d.png)

![image](https://user-images.githubusercontent.com/81119854/128521911-9d7f4976-87bf-45f6-a8bf-604396aebaf6.png)

![image](https://user-images.githubusercontent.com/81119854/128521969-bb29f062-22bd-4abc-b7f2-a51093de20b7.png)

![image](https://user-images.githubusercontent.com/81119854/128522060-ace6b422-6104-481a-bda4-2f113994d7e5.png)

![image](https://user-images.githubusercontent.com/81119854/128522221-cf243a88-c5aa-46ea-9d16-5443da20eb05.png)

[Japan,position number]

![image](https://user-images.githubusercontent.com/81119854/128522618-89c5fa8f-bf27-4028-81ac-1a0e56bb7aa3.png)

![image](https://user-images.githubusercontent.com/81119854/128522684-d17f0865-058f-4fe8-adac-3cd8ef1a8597.png)

Column names that are integers (such as the years) might introduce some confusion. For example, when we are referencing the year 2013, one might confuse that when the 2013th positional index.

To avoid this ambuigity, let's convert the column names into strings: '1980' to '2013'.

![image](https://user-images.githubusercontent.com/81119854/128522812-d8427339-4e68-435f-96ea-4be61c2e2ef9.png)

Since we converted the years to string, let's declare a variable that will allow us to easily call upon the full range of years:

![image](https://user-images.githubusercontent.com/81119854/128522961-6aba353d-82ea-4002-86dd-edccd3bfcb09.png)

Filtering based on a criteria

To filter the dataframe based on a condition, we simply pass the condition as a boolean vector.

For example, Let's filter the dataframe to show the data on Asian countries (AreaName = Asia).

![image](https://user-images.githubusercontent.com/81119854/128536195-acad60d1-d574-4273-b7fd-14aa7899acaf.png)

![image](https://user-images.githubusercontent.com/81119854/128536279-af51ed4c-a6b0-4a73-a80e-9f5a34a1d8bd.png)

![image](https://user-images.githubusercontent.com/81119854/128536379-5df4e662-9bf7-4ddc-9396-c04f1725d6cf.png)

Before we proceed: let's review the changes we have made to our dataframe.

![image](https://user-images.githubusercontent.com/81119854/128536519-19c4f255-ec83-4124-afe7-e97fff19f02b.png)

# Visualizing data with Matplotlib

Matplotlib: Standard Python Visualization Library

Matplotlib is a Python 2D plotting library which produces publication quality figures in a variety of hardcopy formats and interactive environments across platforms. Matplotlib can be used in Python scripts, the Python and IPython shell, the jupyter notebook, web application servers, and four graphical user interface toolkits.

Matplotlib.Pyplot

One of the core aspects of Matplotlib is matplotlib.pyplot. It is Matplotlib's scripting layer which we studied in details in the videos about Matplotlib. Recall that it is a collection of command style functions that make Matplotlib work like MATLAB.

Each pyplot function makes some change to a figure: e.g., creates a figure, creates a plotting area in a figure, plots some lines in a plotting area, decorates the plot with labels, etc. In this lab, we will work with the scripting layer to learn how to generate line plots.

Let's start by importing matplotlib and matplotlib.pyplot as follows:

![image](https://user-images.githubusercontent.com/81119854/128537310-6d92491f-d47d-48cc-b066-52693458c41d.png)

We may check if Matplotlib is loaded by doing:

![image](https://user-images.githubusercontent.com/81119854/128537427-12668bb8-454b-4288-b07c-a330b368e004.png)

We also may apply a style to Matplotlib:

![image](https://user-images.githubusercontent.com/81119854/128537566-46395f71-b2a0-4e01-8b95-dcbd42c8fea5.png)

Plotting in pandas
Fortunately, pandas has a built-in implementation of Matplotlib that we can use. Plotting in pandas is as simple as appending a .plot() method to a series or dataframe.

# Line Plots (Series/Dataframe)

What is a line plot and why use it?

A line chart or line plot is a type of plot which displays information as a series of data points called 'markers' connected by straight line segments. It is a basic type of chart common in many fields. Use line plot when you have a continuous data set. These are best suited for trend-based visualizations of data over a period of time.

Let's start with a case study:

In 2010, Haiti suffered a catastrophic magnitude 7.0 earthquake. The quake caused widespread devastation and loss of life and aout three million people were affected by this natural disaster. 

As part of Canada's humanitarian effort, the Government of Canada stepped up its effort in accepting refugees from Haiti. We can quickly visualize this effort using a Line plot:

Question: Plot a line graph of immigration from Haiti using df.plot().

First, we will extract the data series for Haiti.

![image](https://user-images.githubusercontent.com/81119854/128538242-fc09d886-b4a1-4815-abb8-7c40d80ea8d1.png)

Next, we will plot a line plot by appending .plot() to the haiti dataframe.

![image](https://user-images.githubusercontent.com/81119854/128538364-35cfe736-672f-4be5-b2b1-7f3e22034990.png)

pandas automatically populated the x-axis with the index values (years), and the y-axis with the column values (population). However, notice how the years were not displayed because they are of type string. Therefore, let's change the type of the index values to integer for plotting.

Also, let's label the x and y axis using plt.title(), plt.ylabel(), and plt.xlabel() as follows:

![image](https://user-images.githubusercontent.com/81119854/128538717-4b7e93b5-e3cc-4218-88ac-499a5e66c2ad.png)

We can clearly notice how number of immigrants from Haiti spiked up from 2010 as Canada stepped up its efforts to accept refugees from Haiti. Let's annotate this spike in the plot by using the plt.text() method.

![image](https://user-images.githubusercontent.com/81119854/128539039-0788d696-4c5e-4e74-957c-4ac5eb3d8c0f.png)

![image](https://user-images.githubusercontent.com/81119854/128539071-ffb88b2a-8261-4633-b250-c10f5f108b65.png)

![image](https://user-images.githubusercontent.com/81119854/128539246-e8833367-fc37-4577-8bc3-31b4bda78bd3.png)

![image](https://user-images.githubusercontent.com/81119854/128540262-11fb010c-c361-406f-a51e-2bbd8e7d2612.png)

![image](https://user-images.githubusercontent.com/81119854/128540378-42c09b55-03f3-4480-b37c-12704526bb43.png)

![image](https://user-images.githubusercontent.com/81119854/128540435-330e0842-8f32-426b-abc4-434b772d351a.png)

![image](https://user-images.githubusercontent.com/81119854/128540589-60fe7e2c-3bb0-47d7-a265-a07ba3249579.png)

![image](https://user-images.githubusercontent.com/81119854/128540643-48d660c3-f584-441e-bf9f-0e4f15567dc5.png)

Recall that pandas plots the indices on the x-axis and the columns as individual lines on the y-axis. Since df_CI is a dataframe with the country as the index and years as the columns, we must first transpose the dataframe using transpose() method to swap the row and columns.

![image](https://user-images.githubusercontent.com/81119854/128540982-9dce19e2-ad40-4db9-97a7-0d9648017752.png)

pandas will auomatically graph the two countries on the same graph. Go ahead and plot the new transposed dataframe. Make sure to add a title to the plot and label the axes.

![image](https://user-images.githubusercontent.com/81119854/128541327-8cffaa3f-c133-464c-8493-e695c9cdb9d8.png)

From the above plot, we can observe that the China and India have very similar immigration trends through the years.

![image](https://user-images.githubusercontent.com/81119854/128541713-bb181aba-3278-4b7b-9ff8-861dfb6b4383.png)

Line plot is a handy tool to display several dependent variables against one independent variable. However, it is recommended that no more than 5-10 lines on a single graph; any more than that and it becomes difficult to interpret.

![image](https://user-images.githubusercontent.com/81119854/128542102-b2a03790-7e05-40cb-8d0b-824137333fa8.png)

![image](https://user-images.githubusercontent.com/81119854/128542138-6065ce7b-ef37-468e-a570-fdd613a915a4.png)

![image](https://user-images.githubusercontent.com/81119854/128542186-920949ed-c3c7-4217-a040-22c563dcbe55.png)

![image](https://user-images.githubusercontent.com/81119854/128542338-3861b752-105a-407f-96ed-b6c757c082b7.png)

![image](https://user-images.githubusercontent.com/81119854/128542383-1fee9eb8-40e7-4db3-b316-2a137d925c11.png)

There are many other plotting styles available other than the default Line plot, all of which can be accessed by passing kind keyword to plot(). The full list of available plots are as follows:

![image](https://user-images.githubusercontent.com/81119854/128542583-5f7edd01-81c7-475c-8c41-2176b0f9e9eb.png)

# Basic Visualization Tools

Exploring Datasets with pandas and Matplotlib

The course heavily relies on pandas and Numpy for data wrangling, analysis, and visualization. The primary plotting library that we are exploring in the course is Matplotlib.
 
Dataset: Immigration to Canada from 1980 to 2013. The dataset contains annual data on the flows of international migrants as recorded by the countries of destination (but we focus on Canada). The data presents both inflows and outflows according to the place of birth, citizenship or place of previous / next residence both for foreigners and nationals. 

Downloading and Prepping Data

![image](https://user-images.githubusercontent.com/81119854/128712235-710f0285-8a8f-4de9-92f4-76defa1a58d5.png)

Let's download and import our primary Canadian Immigration dataset using pandas's read_excel() method. Normally, before we can do that, we would need to download a module which pandas requires reading in Excel files. This module was openpyxl (formerlly xlrd). 

We have pre-installed this module, so we would not have to worry about that. Otherwise, we would need to run the following line of code to install the openpyxl module:

![image](https://user-images.githubusercontent.com/81119854/128712862-0dd94452-4438-4b71-a0a9-70719f968c24.png)

Download the dataset and read it into a pandas dataframe.

![image](https://user-images.githubusercontent.com/81119854/128713015-0b50b44e-8a79-4d82-bed5-300d8caaf4ce.png)

Let's take a look at the first five items in our dataset.

![image](https://user-images.githubusercontent.com/81119854/128713116-f493bdf8-ff02-481c-916c-895a50e70e33.png)

Let's find out how many entries there are in our dataset.

![image](https://user-images.githubusercontent.com/81119854/128713227-6a6550c7-9d85-467c-9b5d-14ea978aa53d.png)

Clean up data. We will make some modifications to the original dataset to make it easier to create our visualizations.

1. Clean up the dataset to remove columns that are not informative to us for visualization (eg. Type, AREA, REG).

![image](https://user-images.githubusercontent.com/81119854/128713453-668913c9-9bad-4536-89d2-654ea5da6bca.png)

2. Rename some of the columns so that they make sense.

![image](https://user-images.githubusercontent.com/81119854/128713775-3ddd6483-81e2-4814-b433-8d09fd244952.png)

3. For consistency, ensure that all column labels are of type string.

![image](https://user-images.githubusercontent.com/81119854/128714021-0b087d3e-2d96-4a11-9cce-bb978abb488b.png)

Notice how the above line of code returned False when we tested if all the column labels are of type string. So let's change them all to string type.

![image](https://user-images.githubusercontent.com/81119854/128714116-44843408-28e3-4de8-8cb2-2ef74f8d6ec8.png)


