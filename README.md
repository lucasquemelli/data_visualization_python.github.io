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

4. Set the country name as index - useful for quickly looking up countries using .loc method.

![image](https://user-images.githubusercontent.com/81119854/128715763-30b6b7b6-5933-4805-a790-d2d47b246c55.png)

5. Add total column.

![image](https://user-images.githubusercontent.com/81119854/128715902-c4b5015e-6a26-44a5-bb71-5f276d20017c.png)

Now the dataframe has an extra column that presents the total number of immigrants from each country in the dataset from 1980 - 2013. So if we print the dimension of the data, we get:

![image](https://user-images.githubusercontent.com/81119854/128716108-a96cb2b0-2271-406b-aefc-64336b476b19.png)

So now our dataframe has 38 columns instead of 37 columns that we had before.

![image](https://user-images.githubusercontent.com/81119854/128716351-85d9e70b-4d1c-4baf-a5a7-6ed03b9c0d81.png)

Visualizing Data using Matplotlib

Import the matplotlib library.

![image](https://user-images.githubusercontent.com/81119854/128716872-73bcf9a1-7266-4964-9430-dc589a898a0b.png)

Area Plots

In the last module, we created a line plot that visualized the top 5 countries that contribued the most immigrants to Canada from 1980 to 2013. With a little modification to the code, we can visualize this plot as a cumulative plot, also knows as a Stacked Line Plot or Area plot.

![image](https://user-images.githubusercontent.com/81119854/128717434-8bcb076b-9d27-43f7-95f2-b863df4ceddf.png)

Area plots are stacked by default. And to produce a stacked area plot, each column must be either all positive or all negative values (any NaN, i.e. not a number, values will default to 0). To produce an unstacked plot, set parameter stacked to value False.

![image](https://user-images.githubusercontent.com/81119854/128717932-d6a50743-c22e-4a04-b8e0-901d035a018f.png)

![image](https://user-images.githubusercontent.com/81119854/128718037-76bd5076-0214-4079-a203-b076f47b6bd7.png)

The unstacked plot has a default transparency (alpha value) at 0.5. We can modify this value by passing in the alpha parameter.

![image](https://user-images.githubusercontent.com/81119854/128718767-fc93a630-bde8-4119-9b50-628f5aad849b.png)

![image](https://user-images.githubusercontent.com/81119854/128718891-e2696136-f4bd-419f-a508-8fd53e5066c1.png)

Two types of plotting

There are two styles/options of plotting with matplotlib, plotting using the Artist layer and plotting using the scripting layer.

![image](https://user-images.githubusercontent.com/81119854/128739750-32a2a6fa-cd0b-484a-8828-0755b68a2a8b.png)

![image](https://user-images.githubusercontent.com/81119854/128739961-7ea20267-6553-4aad-b307-47127834b6de.png)

This option sometimes is more transparent and flexible to use for advanced plots (in particular when having multiple plots, as you will see later).

In this course, we will stick to the scripting layer, except for some advanced visualizations where we will need to use the artist layer to manipulate advanced aspects of the plots.

![image](https://user-images.githubusercontent.com/81119854/128740305-05655f81-943a-460e-a670-7ca998c1295b.png)

![image](https://user-images.githubusercontent.com/81119854/128740378-af407066-7557-42a2-8de0-221597967349.png)

![image](https://user-images.githubusercontent.com/81119854/128742546-453e3b25-8cba-4b5a-bd0e-1a3903051148.png)

![image](https://user-images.githubusercontent.com/81119854/128742583-18e3d2ea-bbbe-4efd-bbef-3c811e8020e2.png)

![image](https://user-images.githubusercontent.com/81119854/128742641-14f6beb0-7ecf-4568-9377-72ab6478c80e.png)

By changing the ascending to "False", we get another way to answer this:

![image](https://user-images.githubusercontent.com/81119854/128743126-fdbb151a-f85e-44f4-9c81-3e26ef6ccc89.png)

![image](https://user-images.githubusercontent.com/81119854/128743216-31d38d75-8ba9-4474-b177-45108bd69fcc.png)

Notice that when using "ascending = True", we start with the minimum vale of the number of immigrants. Otherwise, when setting "ascending = False", the tail function finds the last five countries with the least number of immigrants - by starting with the highest to the least number. This influences the order of the countries in the graph.  

![image](https://user-images.githubusercontent.com/81119854/128744940-e09f138a-5e8e-425b-9cee-ced83443fb47.png)

![image](https://user-images.githubusercontent.com/81119854/128744993-eddada2e-be91-4ee1-b2ed-a1f5aca77c05.png)

![image](https://user-images.githubusercontent.com/81119854/128745056-7c2f5898-3ddf-43e1-8c18-a3574e6b4dba.png)

Now using the "ascending=False" and the tail function:

![image](https://user-images.githubusercontent.com/81119854/128745336-34a0a048-bf6e-4d52-803c-932e17ac0bcc.png)

![image](https://user-images.githubusercontent.com/81119854/128745406-1d09df26-360e-4947-a9bb-d217b210802e.png)

Histograms

A histogram is a way of representing the frequency distribution of numeric dataset. The way it works is it partitions the x-axis into bins, assigns each data point in our dataset to a bin, and then counts the number of data points that have been assigned to each bin. So the y-axis is the frequency or the number of data points in each bin.

![image](https://user-images.githubusercontent.com/81119854/128757177-3dffcaf9-795a-4c48-bde9-1919b7d675a0.png)

Before we proceed with creating the histogram plot, let's first examine the data split into intervals. To do this, we will use Numpy's histrogram method to get the bin ranges and frequency counts as follows:

![image](https://user-images.githubusercontent.com/81119854/128757377-b1e641ea-3f7d-4958-888c-734eaf5ccb49.png)

![image](https://user-images.githubusercontent.com/81119854/128757563-9b7c1d83-9324-469c-ad41-2aadc603fdb8.png)

By default, the histrogram method breaks up the dataset into 10 bins. The figure below summarizes the bin ranges and the frequency distribution of immigration in 2013. We can see that in 2013:

![image](https://user-images.githubusercontent.com/81119854/128757744-ee2a6f4f-448d-4b6e-93b0-100df338d933.png)

We can easily graph this distribution by passing kind=hist to plot().

![image](https://user-images.githubusercontent.com/81119854/128757830-6cc000ca-63a1-45e8-86ee-11166a25a027.png)

![image](https://user-images.githubusercontent.com/81119854/128757942-e0552a28-facf-4b20-ad22-d76ad3473c9f.png)

In the above plot, the x-axis represents the population range of immigrants in intervals of 3412.9. The y-axis represents the number of countries that contributed to the aforementioned population.

Notice that the x-axis labels do not match with the bin size. This can be fixed by passing in a xticks keyword that contains the list of the bin sizes, as follows:

![image](https://user-images.githubusercontent.com/81119854/128758078-d85ebb6f-fe65-46a4-9a61-c8f6462fa85f.png)

![image](https://user-images.githubusercontent.com/81119854/128758198-0c1e6d18-105b-4e0f-85e4-e7e2aa31d700.png)

We could use df_can['2013'].plot.hist(), instead. In fact, throughout this lesson, using some_data.plot(kind='type_plot', ...) is equivalent to some_data.plot.type_plot(...). That is, passing the type of the plot as argument or method behaves the same.

We can also plot multiple histograms on the same plot.

![image](https://user-images.githubusercontent.com/81119854/128758346-44ff418e-e6d0-4d8b-a253-cce35928e2a5.png)

![image](https://user-images.githubusercontent.com/81119854/128758619-48830911-9269-458d-aae1-461d7722feb2.png)

![image](https://user-images.githubusercontent.com/81119854/128758680-fc0be67a-a01a-4600-af3a-b863eab728ee.png)

![image](https://user-images.githubusercontent.com/81119854/128758775-50130c2a-3062-4b56-9ffc-f1120efd4069.png)

That does not look right. We'll often come across situations like this when creating plots. The solution often lies in how the underlying dataset is structured. Instead of plotting the population frequency distribution of the population for the 3 countries, pandas instead plotted the population frequency distribution for the years.

This can be easily fixed by first transposing the dataset, and then plotting as shown below.

![image](https://user-images.githubusercontent.com/81119854/128759135-5318a5ed-5e88-44d8-a7d7-16e794f5a504.png)

![image](https://user-images.githubusercontent.com/81119854/128759195-1a4b7da3-892a-442d-a390-59c92b01f6af.png)

![image](https://user-images.githubusercontent.com/81119854/128759235-2e402237-1096-4423-9ee2-55e4c0a0815c.png)

Let's make a few modifications to improve the impact and aesthetics of the previous plot:

![image](https://user-images.githubusercontent.com/81119854/128759595-d72abff7-6482-431b-8c68-130b29f9cce3.png)

![image](https://user-images.githubusercontent.com/81119854/128759624-cbac66d4-e8af-4f0e-bbe8-a6e66b26ec20.png)

![image](https://user-images.githubusercontent.com/81119854/128759721-66875dbf-a7d9-4115-b790-62ea0ec48c0d.png)

![image](https://user-images.githubusercontent.com/81119854/128760165-dca3d773-9bca-4c6e-9e01-fd68a66674fe.png)

If we do not want the plots to overlap each other, we can stack them using the stacked parameter. Let's also adjust the min and max x-axis labels to remove the extra gap on the edges of the plot. We can pass a tuple (min,max) using the xlim paramater, as show below.

![image](https://user-images.githubusercontent.com/81119854/128760314-be5cba5a-aa8c-457d-8f4e-a1f3ce43d068.png)

![image](https://user-images.githubusercontent.com/81119854/128760351-af5b6bc7-61c3-4526-889f-477457f8e43f.png)

![image](https://user-images.githubusercontent.com/81119854/128760558-2f79d716-5f83-4e06-ba04-85d29e5b62da.png)

![image](https://user-images.githubusercontent.com/81119854/128761210-65d759d1-0dc2-4043-b5a3-34a2219983f0.png)

![image](https://user-images.githubusercontent.com/81119854/128761245-7162892d-1ac3-4e2c-b005-78d690057392.png)

Bar Charts (Dataframe)

A bar plot is a way of representing data where the length of the bars represents the magnitude/size of the feature/variable. Bar graphs usually represent numerical and categorical variables grouped in intervals.

To create a bar plot, we can pass one of two arguments via kind parameter in plot():

![image](https://user-images.githubusercontent.com/81119854/128763226-dc3caa15-87ac-4992-ad49-cbcb7e5a0179.png)

Vertical bar plot

In vertical bar graphs, the x-axis is used for labelling, and the length of bars on the y-axis corresponds to the magnitude of the variable being measured. Vertical bar graphs are particularly useful in analyzing time series data. One disadvantage is that they lack space for text labelling at the foot of each bar.

Let's start off by analyzing the effect of Iceland's Financial Crisis:

The 2008 - 2011 Icelandic Financial Crisis was a major economic and political event in Iceland. Relative to the size of its economy, Iceland's systemic banking collapse was the largest experienced by any country in economic history. The crisis led to a severe economic depression in 2008 - 2011 and significant political unrest.

![image](https://user-images.githubusercontent.com/81119854/128763564-ddcd57da-0662-4e88-9129-2382cd1c3cd7.png)

![image](https://user-images.githubusercontent.com/81119854/128763633-6f730e52-006e-42e3-9552-c9cc3702b8e5.png)

![image](https://user-images.githubusercontent.com/81119854/128763695-d764e8ad-573e-4089-891f-901cd1eed2c5.png)

![image](https://user-images.githubusercontent.com/81119854/128763729-6f8be934-98b8-47e2-b4d2-588e71b966c8.png)

The bar plot above shows the total number of immigrants broken down by each year. We can clearly see the impact of the financial crisis; the number of immigrants to Canada started increasing rapidly after 2008.

Let's annotate this on the plot using the annotate method of the scripting layer or the pyplot interface. We will pass in the following parameters:

![image](https://user-images.githubusercontent.com/81119854/128764080-66ae9a16-0baf-4fe0-8f28-4e0103edd083.png)

![image](https://user-images.githubusercontent.com/81119854/128764463-7b832d5d-4b95-4593-9451-f999a2507974.png)

![image](https://user-images.githubusercontent.com/81119854/128764506-c7b89d0c-5369-4d26-943f-b0626d804bf9.png)

Let's also annotate a text to go over the arrow. We will pass in the following additional parameters:

![image](https://user-images.githubusercontent.com/81119854/128764584-2d2f3708-7e13-4a84-92c4-67f01144e44c.png)

![image](https://user-images.githubusercontent.com/81119854/128764629-8ca1cf43-3e04-4b79-a3c6-71b229193849.png)

![image](https://user-images.githubusercontent.com/81119854/128764671-58ec65de-cabf-46e2-8274-e480fa5e2dcd.png)

Horizontal Bar Plot

Sometimes it is more practical to represent the data horizontally, especially if you need more room for labelling the bars. In horizontal bar graphs, the y-axis is used for labelling, and the length of bars on the x-axis corresponds to the magnitude of the variable being measured. As you will see, there is more room on the y-axis to label categorical variables.

![image](https://user-images.githubusercontent.com/81119854/128764796-b5be12c4-07bb-4753-b909-8494388cad5e.png)

Step 1: Get the data pertaining to the top 15 countries.

![image](https://user-images.githubusercontent.com/81119854/128765241-13901bb6-b5fd-4cff-bba7-20825d9d095c.png)

Step 2: Plot data:

![image](https://user-images.githubusercontent.com/81119854/128765307-dca091aa-7447-4c80-9dc6-84fbe09a1744.png)

![image](https://user-images.githubusercontent.com/81119854/128767522-5323402b-5307-493d-84b9-ef3e1070e961.png)

![image](https://user-images.githubusercontent.com/81119854/128767602-50943b10-9ca4-4357-af77-a9171255949c.png)

In order to use the function annotate, try:

#annotate value labels to each country
for index, value in enumerate(df_top15): 
        label = format(int(value), ',') # format int with commas
#place text at the end of bar (subtracting 47000 from x, and 0.1 from y to make it fit within the bar)
        plt.annotate(label, xy=(value - 47000, index - 0.10), color='white')

Changing the color of the bars:

![image](https://user-images.githubusercontent.com/81119854/128767836-0914f94e-688e-4b57-84d9-b83d491bb927.png)

![image](https://user-images.githubusercontent.com/81119854/128767877-dc13d4a5-6147-4156-b83e-a8535bbd2a86.png)

# Specialized Visualization Tools: Pie Charts, Box Plots, Scatter Plots, and Bubble Plots

![image](https://user-images.githubusercontent.com/81119854/128773508-1f6f65fb-3024-447d-90e0-16162578697d.png)

Download the dataset and read it into a pandas dataframe.

![image](https://user-images.githubusercontent.com/81119854/128773598-2ea5c6ec-f265-41be-8c9a-8ab21f5dc7b4.png)

Let's take a look at the first five items in our dataset.

![image](https://user-images.githubusercontent.com/81119854/128773644-ee13365f-c3fc-4f3b-a279-cfbc379563be.png)

Let's find out how many entries there are in our dataset.

![image](https://user-images.githubusercontent.com/81119854/128773716-7815160f-a566-4c7e-8334-63c1a34d4395.png)

Clean up data. We will make some modifications to the original dataset to make it easier to create our visualizations.

![image](https://user-images.githubusercontent.com/81119854/128773886-faff8fb6-5396-48bd-afe4-59a92d9ab329.png)

Visualizing Data using Matplotlib

![image](https://user-images.githubusercontent.com/81119854/128773953-89d4f61c-405a-4022-b11e-28460e7edcce.png)

Pie Charts 

A pie chart is a circular graphic that displays numeric proportions by dividing a circle (or pie) into proportional slices. You are most likely already familiar with pie charts as it is widely used in business and media. We can create pie charts in Matplotlib by passing in the kind=pie keyword.

Let's use a pie chart to explore the proportion (percentage) of new immigrants grouped by continents for the entire time period from 1980 to 2013.

Step 1: Gather data.

![image](https://user-images.githubusercontent.com/81119854/128774265-a3dc3d0a-96ab-4c7d-9978-eb8eddaa01dd.png)

![image](https://user-images.githubusercontent.com/81119854/128774304-52d01841-6f88-4dc3-8798-ef931690359b.png)

![image](https://user-images.githubusercontent.com/81119854/128774468-ad9ff68a-3ec6-41ba-bf33-678bf719ea07.png)

![image](https://user-images.githubusercontent.com/81119854/128774588-064de690-ae13-4058-b14f-eac943ef6836.png)

Step 2: Plot the data. We will pass in kind = 'pie' keyword, along with the following additional parameters:

![image](https://user-images.githubusercontent.com/81119854/128774684-8df04589-3681-4463-b866-df1a42d6a1d5.png)

![image](https://user-images.githubusercontent.com/81119854/128775121-23fb444e-0677-41d3-a56e-fb618c7b9d69.png)

![image](https://user-images.githubusercontent.com/81119854/128775144-b0a10faa-02e2-46d3-bbe0-5902d874857f.png)

The above visual is not very clear, the numbers and text overlap in some instances. Let's make a few modifications to improve the visuals:

![image](https://user-images.githubusercontent.com/81119854/128775207-25b99cba-d62d-41fa-b269-2afca00c6287.png)

![image](https://user-images.githubusercontent.com/81119854/128775430-f160e8c9-6615-4203-a3e0-6554c5d03a7d.png)

![image](https://user-images.githubusercontent.com/81119854/128775477-6c69fa67-c50b-4e47-80c6-2604614e2276.png)

![image](https://user-images.githubusercontent.com/81119854/128778837-5bf8a73a-db87-4ec9-8e3a-00cd71584ce4.png)

![image](https://user-images.githubusercontent.com/81119854/128779175-d2b12aa5-27a0-4e77-85d1-7f581bcf820e.png)

![image](https://user-images.githubusercontent.com/81119854/128779248-a8708aed-0c5c-4073-aa42-7d33f53df2da.png)

Box Plots

![image](https://user-images.githubusercontent.com/81119854/128779475-77ef2447-77b6-44c5-adfc-34a473f68fd5.png)

![image](https://user-images.githubusercontent.com/81119854/128779528-193bc0a1-71a4-4605-aa87-d9f2590b5bf0.png)

To make a boxplot, we can use kind=box in plot method invoked on a pandas series or dataframe.

Let's plot the box plot for the Japanese immigrants between 1980 - 2013.

Step 1: Get the subset of the dataset. Even though we are extracting the data for just one country, we will obtain it as a dataframe. This will help us with calling the dataframe.describe() method to view the percentiles.

![image](https://user-images.githubusercontent.com/81119854/128779866-1551acf4-e3f6-44e3-8dd3-a0c4c51197d6.png)

Step 2: Plot by passing in kind='box'.

![image](https://user-images.githubusercontent.com/81119854/128779976-bc9ce582-112d-483e-a6ea-846be36b2cef.png)

![image](https://user-images.githubusercontent.com/81119854/128779996-3d414fc3-8084-439d-b541-18f6b52bf645.png)

We can immediately make a few key observations from the plot above:

1. The minimum number of immigrants is around 200 (min), maximum number is around 1300 (max), and median number of immigrants is around 900 (median).
2. 25% of the years for period 1980 - 2013 had an annual immigrant count of ~500 or fewer (First quartile).
3. 75% of the years for period 1980 - 2013 had an annual immigrant count of ~1100 or fewer (Third quartile).

We can view the actual numbers by calling the describe() method on the dataframe.

![image](https://user-images.githubusercontent.com/81119854/128780251-954f2b36-771f-4a31-87e2-dc1ff8563dcf.png)

One of the key benefits of box plots is comparing the distribution of multiple datasets. In one of the previous labs, we observed that China and India had very similar immigration trends. Let's analyze these two countries further using box plots.

![image](https://user-images.githubusercontent.com/81119854/128869046-a630199f-be65-4364-aced-e6a24a78de72.png)

Step 1: Get the dataset for China and India and call the dataframe df_CI.

![image](https://user-images.githubusercontent.com/81119854/128869712-44cb149e-d599-4817-a121-a85bf1b8c097.png)

Let's view the percentiles associated with both countries using the describe() method.

![image](https://user-images.githubusercontent.com/81119854/128869853-07e08e79-cf2c-4a50-a021-ded1fe4bc895.png)

Step 2: Plot data.

![image](https://user-images.githubusercontent.com/81119854/128870316-ec483bf0-9977-4c2f-a021-bafd06da0181.png)

![image](https://user-images.githubusercontent.com/81119854/128870368-8dc0f446-6746-4d45-a39f-5d6877ea5d78.png)

We can observe that, while both countries have around the same median immigrant population (~20,000), China's immigrant population range is more spread out than India's. The maximum population from India for any year (36,210) is around 15% lower than the maximum population from China (42,584).

If we prefer to create horizontal box plots, we can pass the vert parameter in the plot function and assign it to False. We can also specify a different color.

![image](https://user-images.githubusercontent.com/81119854/128870701-3fe44ca5-a922-46f8-90d0-52cc262e74af.png)

![image](https://user-images.githubusercontent.com/81119854/128870742-8506fad0-e2c4-48c4-8119-744bb8f4ad07.png)

Subplots

Often times we might want to plot multiple plots within the same figure. For example, we might want to perform a side by side comparison of the box plot with the line plot of China and India's immigration.

To visualize multiple plots together, we can create a figure (overall canvas) and divide it into subplots, each containing a plot. With subplots, we usually work with the artist layer instead of the scripting layer.

![image](https://user-images.githubusercontent.com/81119854/128871293-02839d13-004a-42d3-af69-ca73220ae05b.png)

![image](https://user-images.githubusercontent.com/81119854/128871326-5468e7af-fca1-4acb-b14e-5a5fa4252c36.png)

We can then specify which subplot to place each plot by passing in the ax paramemter in plot() method as follows:

![image](https://user-images.githubusercontent.com/81119854/128871898-f79baa81-81a1-4b76-8b0a-1c4b13441eea.png)

![image](https://user-images.githubusercontent.com/81119854/128871955-9c7caa11-67b3-4afc-9103-13c481f4930b.png)

nrows * ncol = plot_number -> the plot_number is the layout of the graph. In this case, there are two graphs side by side: 2 columns and 1 line. Line: two graphs. Column 1: box plot. Column 2: line.

![image](https://user-images.githubusercontent.com/81119854/128877934-eb343782-5ca3-4bd1-8e9a-7b903aee1f60.png)

Let's try something a little more advanced.

Previously we identified the top 15 countries based on total immigration from 1980 - 2013.

![image](https://user-images.githubusercontent.com/81119854/128878064-1d7f62e6-e945-47fe-941a-191923a8e9c1.png)

Step 1: Get the dataset. Get the top 15 countries based on Total immigrant population. Name the dataframe df_top15.

![image](https://user-images.githubusercontent.com/81119854/128878337-289399e2-ff51-4650-9c42-87edb9a99b0d.png)

Step 2: Create a new dataframe which contains the aggregate for each decade. One way to do that:

1. Create a list of all years in decades 80's, 90's, and 00's.
2. Slice the original dataframe df_can to create a series for each decade and sum across all years for each country.
3. Merge the three series into a new data frame. Call your dataframe new_df.

![image](https://user-images.githubusercontent.com/81119854/128878951-efa2c6e1-2e2b-4661-868d-fae755614d7b.png)

![image](https://user-images.githubusercontent.com/81119854/128878992-3ee72bb7-c5eb-4a8b-a4bd-10c7ae216788.png)

Let's learn more about the statistics associated with the dataframe using the describe() method.

![image](https://user-images.githubusercontent.com/81119854/128879587-22ae71f8-b5c3-4bb5-9ed5-6474ebc51b8d.png)

Step 3: Plot the box plots.

![image](https://user-images.githubusercontent.com/81119854/128880614-a2e65376-1346-416d-966e-700e3a7643cf.png)

![image](https://user-images.githubusercontent.com/81119854/128880661-03d5f331-bbd3-41d6-83e4-ed99468d7246.png)

Note how the box plot differs from the summary table created. The box plot scans the data and identifies the outliers. In order to be an outlier, the data value must be:

![image](https://user-images.githubusercontent.com/81119854/128881124-fa7eab08-b81a-4bfc-bd94-2883f43422f3.png)

Let's look at decade 2000s as an example:

![image](https://user-images.githubusercontent.com/81119854/128881174-1bf964e8-4f5b-4f93-b4ca-278fca427d89.png)

Using the definition of outlier, any value that is greater than Q3 by 1.5 times IQR will be flagged as outlier.

Outlier > 105,505.5 + (1.5 * 69,404)
Outlier > 209,611.5

![image](https://user-images.githubusercontent.com/81119854/128881421-e5b5af7e-6913-4829-a2a7-d8075d54a186.png)

Scatter Plots

A scatter plot (2D) is a useful method of comparing variables against each other. Scatter plots look similar to line plots in that they both map independent and dependent variables on a 2D graph. While the data points are connected together by a line in a line plot, they are not connected in a scatter plot. 

The data in a scatter plot is considered to express a trend. With further analysis using tools like regression, we can mathematically calculate this relationship and use it to predict trends outside the dataset.

Let's start by exploring the following:

Using a scatter plot, let's visualize the trend of total immigrantion to Canada (all countries combined) for the years 1980 - 2013.

Step 1: Get the dataset. Since we are expecting to use the relationship betewen years and total population, we will convert years to int type.

![image](https://user-images.githubusercontent.com/81119854/128895700-24cd921c-168e-432f-8291-511259057ebc.png)

Step 2: Plot the data. In Matplotlib, we can create a scatter plot set by passing in kind='scatter' as plot argument. We will also need to pass in x and y keywords to specify the columns that go on the x- and the y-axis.

![image](https://user-images.githubusercontent.com/81119854/128895815-d86d2be7-a86c-4a45-a318-3010af97657a.png)

Notice how the scatter plot does not connect the data points together. We can clearly observe an upward trend in the data: as the years go by, the total number of immigrants increases. We can mathematically analyze this upward trend using a regression line (line of best fit).

So let's try to plot a linear line of best fit, and use it to predict the number of immigrants in 2015.

![image](https://user-images.githubusercontent.com/81119854/128897001-a530ce16-73f6-4352-98ec-7bbf4f732126.png)

![image](https://user-images.githubusercontent.com/81119854/128897129-748a4438-bf79-4dfc-8cf7-71c3c0813fc3.png)

The output is an array with the polynomial coefficients, highest powers first. Since we are plotting a linear regression y= a * x + b, our output has 2 elements [5.56709228e+03, -1.09261952e+07] with the the slope in position 0 and intercept in position 1.

Step 2: Plot the regression line on the scatter plot.

![image](https://user-images.githubusercontent.com/81119854/128897595-2963126b-bef8-444e-a337-3edb585b577b.png)

![image](https://user-images.githubusercontent.com/81119854/128897649-ce0febe9-af9e-4095-9908-b34229eeb998.png)

Using the equation of line of best fit, we can estimate the number of immigrants in 2015:

![image](https://user-images.githubusercontent.com/81119854/128897828-d1280051-47c3-43f3-865e-1367bce775c0.png)

When compared to the actual from Citizenship and Immigration Canada's (CIC) 2016 Annual Report, we see that Canada accepted 271,845 immigrants in 2015. Our estimated value of 291,310 is within 7% of the actual number, which is pretty good considering our original data came from United Nations (and might differ slightly from CIC data).

As a side note, we can observe that immigration took a dip around 1993 - 1997. Further analysis into the topic revealed that in 1993 Canada introcuded Bill C-86 which introduced revisions to the refugee determination system, mostly restrictive. Further amendments to the Immigration Regulations cancelled the sponsorship required for "assisted relatives" and reduced the points awarded to them, making it more difficult for family members (other than nuclear family) to immigrate to Canada. These restrictive measures had a direct impact on the immigration numbers for the next several years.

![image](https://user-images.githubusercontent.com/81119854/128898380-5512e44f-d553-4af3-8472-4fe85b8c6457.png)

![image](https://user-images.githubusercontent.com/81119854/128900382-e205e3cf-91cf-4b15-b689-859876c708f1.png)

![image](https://user-images.githubusercontent.com/81119854/128900439-96502982-c150-4a11-b739-31ed331dc9c1.png)

![image](https://user-images.githubusercontent.com/81119854/128900683-ead8e343-2cff-4fdb-a81e-9669312d8304.png)

![image](https://user-images.githubusercontent.com/81119854/128900732-abfb3dbe-9f8f-4141-b543-1e4d3c70db6f.png)

Bubble Plots 

A bubble plot is a variation of the scatter plot that displays three dimensions of data (x, y, z). The data points are replaced with bubbles, and the size of the bubble is determined by the third variable z, also known as the weight. In maplotlib, we can pass in an array or scalar to the parameter s to plot(), that contains the weight of each point.

Let's start by analyzing the effect of Argentina's great depression.

Argentina suffered a great depression from 1998 to 2002, which caused widespread unemployment, riots, the fall of the government, and a default on the country's foreign debt. In terms of income, over 50% of Argentines were poor, and seven out of ten Argentine children were poor at the depth of the crisis in 2002.

Let's analyze the effect of this crisis, and compare Argentina's immigration to that of it's neighbour Brazil. Let's do that using a bubble plot of immigration from Brazil and Argentina for the years 1980 - 2013. We will set the weights for the bubble as the normalized value of the population for each year.

Step 1: Get the data for Brazil and Argentina. Like in the previous example, we will convert the Years to type int and include it in the dataframe.

![image](https://user-images.githubusercontent.com/81119854/128903517-99ea0abf-1c3d-4fce-a6b8-6a9ff3bf8f2c.png)

Step 2: Create the normalized weights.

There are several methods of normalizations in statistics, each with its own use. In this case, we will use feature scaling to bring all values into the range [0, 1]. The general formula is:

![image](https://user-images.githubusercontent.com/81119854/128903646-cccdbd65-7966-4eb3-b114-c1a9bdb553e2.png)

where  𝑋  is the original value,  𝑋′  is the corresponding normalized value. The formula sets the max value in the dataset to 1, and sets the min value to 0. The rest of the data points are scaled to a value between 0-1 accordingly.

![image](https://user-images.githubusercontent.com/81119854/128903789-bd215571-fe3d-40f0-a918-4a68bb332de0.png)

Step 3: Plot the data.

![image](https://user-images.githubusercontent.com/81119854/128903905-0e0c14a3-ac5b-4a3d-9c03-9f899c2507c4.png)

![image](https://user-images.githubusercontent.com/81119854/128904118-9a733bfc-b9be-4569-a301-243e2c47a2c4.png)

![image](https://user-images.githubusercontent.com/81119854/128904227-0cae6b48-faeb-4530-8418-7db419141aad.png)

The size of the bubble corresponds to the magnitude of immigrating population for that year, compared to the 1980 - 2013 data. The larger the bubble is, the more immigrants are in that year.

From the plot above, we can see a corresponding increase in immigration from Argentina during the 1998 - 2002 great depression. We can also observe a similar spike around 1985 to 1993. In fact, Argentina had suffered a great depression from 1974 to 1990, just before the onset of 1998 - 2002 great depression.

On a similar note, Brazil suffered the Samba Effect where the Brazilian real (currency) dropped nearly 35% in 1999. There was a fear of a South American financial crisis as many South American countries were heavily dependent on industrial exports from Brazil. The Brazilian government subsequently adopted an austerity program, and the economy slowly recovered over the years, culminating in a surge in 2010. The immigration data reflect these events.

![image](https://user-images.githubusercontent.com/81119854/128904644-cf63078d-97f7-435a-ad45-298fd420fa41.png)

Step 1: Normalize the data pertaining to China and India.

![image](https://user-images.githubusercontent.com/81119854/128904807-9b306d14-e086-41e0-8415-27ca694950be.png)

Step 2: Generate the bubble plots.

![image](https://user-images.githubusercontent.com/81119854/128905122-5362147d-089f-436f-a367-aec0bd3330d7.png)

![image](https://user-images.githubusercontent.com/81119854/128905186-5af2c0f2-359f-4995-b882-b5f85e527058.png)

# Advanced Visualization Tools: Waffle Charts, Word Clouds, and Regression Plots

Downloading and Prepping Data

Import Primary Modules:

![image](https://user-images.githubusercontent.com/81119854/128942733-d1ec3ed5-a26f-4db8-aa73-80f29f908788.png)

Download the dataset and read it into a pandas dataframe:

![image](https://user-images.githubusercontent.com/81119854/128942867-5e37d320-5edc-4e9f-84c3-de6a3193a515.png)

![image](https://user-images.githubusercontent.com/81119854/128942912-7047d9bb-2915-4382-8958-3ef27afbc3a6.png)

How many entries there are in our dataset?

![image](https://user-images.githubusercontent.com/81119854/128942991-74ee509c-2735-471e-9758-77ca0a348cf9.png)

Clean up data. We will make some modifications to the original dataset to make it easier to create our visualizations.

![image](https://user-images.githubusercontent.com/81119854/128943215-55720c2d-f144-4526-8241-9cb697c8b65b.png)

Visualizing Data using Matplotlib

Import and setup matplotlib:

![image](https://user-images.githubusercontent.com/81119854/128944208-f9c7594c-41a0-4c7c-9642-c542885e4cfd.png)

Waffle Charts

A waffle chart is an interesting visualization that is normally created to display progress toward goals. It is commonly an effective option when you are trying to add interesting visualization features to a visual that consists mainly of cells, such as an Excel dashboard.

Let's revisit the previous case study about Denmark, Norway, and Sweden.

![image](https://user-images.githubusercontent.com/81119854/128944357-05693960-8ee9-48d7-aea6-75f9766e64c0.png)

Unfortunately, unlike R, waffle charts are not built into any of the Python visualization libraries. Therefore, we will learn how to create them from scratch.

Step 1. The first step into creating a waffle chart is determing the proportion of each category with respect to the total.

![image](https://user-images.githubusercontent.com/81119854/128944558-c2acef48-6554-408a-b5da-d1a4709591dd.png)

Step 2. The second step is defining the overall size of the waffle chart.

![image](https://user-images.githubusercontent.com/81119854/128944655-3bd809a7-1010-4dff-89c7-df99d4157a46.png)

Step 3. The third step is using the proportion of each category to determine its respective number of tiles.

![image](https://user-images.githubusercontent.com/81119854/128944835-2b17aed4-9eee-4d56-aa43-66dfd8616290.png)

Based on the calculated proportions, Denmark will occupy 129 tiles of the waffle chart, Norway will occupy 77 tiles, and Sweden will occupy 194 tiles.

Step 4. The fourth step is creating a matrix that resembles the waffle chart and populating it.

![image](https://user-images.githubusercontent.com/81119854/128944982-ecc07a3e-fb33-448f-93c5-e9064e2c46ae.png)

Let's take a peek at how the matrix looks like.

![image](https://user-images.githubusercontent.com/81119854/128945061-1d325826-a2cc-4f6e-9238-2d0656251ffa.png)

As expected, the matrix consists of three categories and the total number of each category's instances matches the total number of tiles allocated to each category.

Step 5. Map the waffle chart matrix into a visual.

![image](https://user-images.githubusercontent.com/81119854/128945158-7d70fe13-1eab-497f-a92e-75704be91ab5.png)

Step 6. Prettify the chart.

![image](https://user-images.githubusercontent.com/81119854/128945311-001e777e-16f1-431e-8124-af7236c2155e.png)

![image](https://user-images.githubusercontent.com/81119854/128945376-95bce791-0469-4d0e-bd06-e948e272d7a8.png)

Step 7. Create a legend and add it to chart.

![image](https://user-images.githubusercontent.com/81119854/128945438-2ed17a04-21b1-4f97-9fef-0420f7e64959.png)
![image](https://user-images.githubusercontent.com/81119854/128945463-ecfb96a6-234e-4904-a7ca-6e185b56eb94.png)

![image](https://user-images.githubusercontent.com/81119854/128945495-9b1fc97a-7d58-48bc-8aef-399e6366b43d.png)

Now it would very inefficient to repeat these seven steps every time we wish to create a waffle chart. So let's combine all seven steps into one function called create_waffle_chart. This function would take the following parameters as input:

![image](https://user-images.githubusercontent.com/81119854/128945570-27298626-1cd4-40ca-b8b5-32c6d185e003.png)

![image](https://user-images.githubusercontent.com/81119854/128945672-5aef1119-bdfd-4cbb-9d63-8b0315aa0384.png)
![image](https://user-images.githubusercontent.com/81119854/128945708-f9e04756-8dbe-46d2-b3db-f6cd43eb0f19.png)
![image](https://user-images.githubusercontent.com/81119854/128945746-78a84a36-7cb8-4dfd-a60a-3f28b6446c91.png)

Now to create a waffle chart, all we have to do is call the function create_waffle_chart. Let's define the input parameters:

![image](https://user-images.githubusercontent.com/81119854/128945785-661035a4-cf33-4a6c-ad09-00b4c4b4d5c6.png)

And now let's call our function to create a waffle chart.

![image](https://user-images.githubusercontent.com/81119854/128945822-782a0a42-2e4e-4319-b390-e6fad55c3a00.png)

There seems to be a new Python package for generating waffle charts called PyWaffle.

Word Clouds

Word clouds (also known as text clouds or tag clouds) work in a simple way: the more a specific word appears in a source of textual data (such as a speech, blog post, or database), the bigger and bolder it appears in the word cloud.

Luckily, a Python package already exists in Python for generating word clouds. The package, called word_cloud was developed by Andreas Mueller.

Let's use this package to learn how to generate a word cloud for a given text document.

First, let's install the package.

![image](https://user-images.githubusercontent.com/81119854/129034380-609a4974-5663-4896-bbb5-974efd20043b.png)

![image](https://user-images.githubusercontent.com/81119854/129035258-6a8a32a1-8a71-4104-82b2-1f505cd0fe0c.png)

Word clouds are commonly used to perform high-level analysis and visualization of text data. Accordinly, let's digress from the immigration dataset and work with an example that involves analyzing text data. Let's try to analyze a short novel written by Lewis Carroll titled Alice's Adventures in Wonderland. Let's go ahead and download a .txt file of the novel.

![image](https://user-images.githubusercontent.com/81119854/129035413-b23fcb1d-ae45-4545-bdc4-3a99c7aee452.png)
![image](https://user-images.githubusercontent.com/81119854/129035599-f47bc02b-ebb5-43e2-a3d3-3145d52fb662.png)

Next, let's use the stopwords that we imported from word_cloud. We use the function set to remove any redundant stopwords.

![image](https://user-images.githubusercontent.com/81119854/129035830-df03c162-1ab8-4bdd-9dd7-3cbb487dd9d3.png)

Create a word cloud object and generate a word cloud. For simplicity, let's generate a word cloud using only the first 2000 words in the novel.

![image](https://user-images.githubusercontent.com/81119854/129036159-f6d6f760-91df-4615-9fa5-9a09afef2bf8.png)

Awesome! Now that the word cloud is created, let's visualize it.

![image](https://user-images.githubusercontent.com/81119854/129036286-5d0ccbce-7dec-4c02-b1e4-5761991c4774.png)

Interesting! So in the first 2000 words in the novel, the most common words are Alice, said, little, Queen, and so on. Let's resize the cloud so that we can see the less frequent words a little better.

![image](https://user-images.githubusercontent.com/81119854/129036602-58ac729d-6b2c-43c4-b0fe-6545a545bd5c.png)

![image](https://user-images.githubusercontent.com/81119854/129036661-3750c2f8-6b18-46ce-a7cd-a56096988f7a.png)

Much better! However, said isn't really an informative word. So let's add it to our stopwords and re-generate the cloud.

![image](https://user-images.githubusercontent.com/81119854/129036884-d740666f-f37a-47bd-bd07-dbcb394ab1d4.png)

![image](https://user-images.githubusercontent.com/81119854/129036949-99df35c8-b4a3-4f82-90c3-68e4927f9157.png)

Excellent! This looks really interesting! Another cool thing we can implement with the word_cloud package is superimposing the words onto a mask of any shape. Let's use a mask of Alice and her rabbit. The mask is already created, so let's go ahead and download it and call it alice_mask.png.

![image](https://user-images.githubusercontent.com/81119854/129037422-c55a6e77-9d9d-4e03-a858-6745f5cffeb2.png)

Let's take a look at how the mask looks like.

![image](https://user-images.githubusercontent.com/81119854/129037539-48d548a3-5524-4fbf-91d7-07a620972ac6.png)

![image](https://user-images.githubusercontent.com/81119854/129037630-926556da-851a-42d3-b5b0-ac00f6d7da1a.png)

Shaping the word cloud according to the mask is straightforward using word_cloud package. For simplicity, we will continue using the first 2000 words in the novel.

![image](https://user-images.githubusercontent.com/81119854/129037887-1b97f7d1-7aa4-4fd5-9a16-abfa26239d82.png)

![image](https://user-images.githubusercontent.com/81119854/129038212-41b3e00a-1ae2-4910-af90-3919cea3d41b.png)

Unfortunately, our immigration data does not have any text data, but where there is a will there is a way. Let's generate sample text data from our immigration dataset, say text data of 90 words.

Let's recall how our data looks like.

![image](https://user-images.githubusercontent.com/81119854/129038451-4094f89f-ad0d-4f32-a8d8-e3278831a191.png)

And what was the total immigration from 1980 to 2013?

![image](https://user-images.githubusercontent.com/81119854/129038560-9dc2ee0d-96ff-4667-a5f9-ada180d0a423.png)

Using countries with single-word names, let's duplicate each country's name based on how much they contribute to the total immigration.

![image](https://user-images.githubusercontent.com/81119854/129039362-a9b131de-5e75-4307-bec2-d84129ec325d.png)

We are not dealing with any stopwords here, so there is no need to pass them when creating the word cloud.

![image](https://user-images.githubusercontent.com/81119854/129039517-33dc6875-14e4-4207-b668-6a993b200b1c.png)

![image](https://user-images.githubusercontent.com/81119854/129039600-bda2f089-ac60-48b1-b167-8946a16a793b.png)

![image](https://user-images.githubusercontent.com/81119854/129039676-362ab1ae-1580-4d52-8f13-216690fc48b2.png)

According to the above word cloud, it looks like the majority of the people who immigrated came from one of 15 countries that are displayed by the word cloud. One cool visual that we could build, is perhaps the map of Canada and a mask and superimposing the word cloud on top of the map of Canada. 

Regression Plots

Seaborn is a Python visualization library based on matplotlib. It provides a high-level interface for drawing attractive statistical graphics. 

In lab Pie Charts, Box Plots, Scatter Plots, and Bubble Plots, we learned how to create a scatter plot and then fit a regression line. It took ~20 lines of code to create the scatter plot along with the regression fit. In this final section, we will explore seaborn and see how efficient it is to create regression lines and fits using this library!

Let's first install seaborn

![image](https://user-images.githubusercontent.com/81119854/129042011-38a601d5-e212-401a-beff-5e5614c874c0.png)

![image](https://user-images.githubusercontent.com/81119854/129042093-6b1f4747-3d85-48e9-b70b-8a421e34151e.png)

![image](https://user-images.githubusercontent.com/81119854/129042150-7abb281a-6ed4-4c5f-8e35-3c9f93c4f9df.png)

Create a new dataframe that stores that total number of landed immigrants to Canada per year from 1980 to 2013.

![image](https://user-images.githubusercontent.com/81119854/129042355-b4e91bf6-1b40-4209-848c-5259a409c423.png)

![image](https://user-images.githubusercontent.com/81119854/129042403-c2cffd0a-5718-4f41-9fca-9ecbb98b8fb6.png)

With seaborn, generating a regression plot is as simple as calling the regplot function.

![image](https://user-images.githubusercontent.com/81119854/129042516-4c0f95be-4e44-4de8-868e-3705add4a51a.png)

This is not magic; it is seaborn! You can also customize the color of the scatter plot and regression line. Let's change the color to green.

![image](https://user-images.githubusercontent.com/81119854/129042614-25fc6dc1-1f2b-4b8a-84a6-0fb3b17d7f56.png)

You can always customize the marker shape, so instead of circular markers, let's use +.

![image](https://user-images.githubusercontent.com/81119854/129042719-c80ad8cf-af44-480f-96ba-bee905566182.png)

Let's blow up the plot a little so that it is more appealing to the sight.

![image](https://user-images.githubusercontent.com/81119854/129042886-853873e8-5eda-4614-85d5-c2ab0e6e82f9.png)

![image](https://user-images.githubusercontent.com/81119854/129042963-b000b385-1780-46a4-b687-27fe526d0983.png)

And let's increase the size of markers so they match the new size of the figure, and add a title and x- and y-labels.

![image](https://user-images.githubusercontent.com/81119854/129043137-316fdb34-d5b6-45c8-8861-ccc8a2cb7615.png)

![image](https://user-images.githubusercontent.com/81119854/129043228-cb08438b-d7e5-413c-9abc-265ffe538849.png)

And finally increase the font size of the tickmark labels, the title, and the x- and y-labels so they don't feel left out!

![image](https://user-images.githubusercontent.com/81119854/129043538-87467c68-4c47-4a2b-ada1-03d5109acb2b.png)

![image](https://user-images.githubusercontent.com/81119854/129043643-85e2b1d0-c21b-4fda-ab70-4dcc42dc2019.png)

If we are not a big fan of the purple background, we can easily change the style to a white plain background.

![image](https://user-images.githubusercontent.com/81119854/129043806-55da4ed1-6215-47a2-a667-fc06bf4c39f9.png)

![image](https://user-images.githubusercontent.com/81119854/129044417-9b3f9c57-7bb7-4990-b604-446859749ae4.png)

Or to a white background with gridlines.

![image](https://user-images.githubusercontent.com/81119854/129044011-dabe0c55-697f-45ac-bb8f-d21c0133e1d5.png)

![image](https://user-images.githubusercontent.com/81119854/129044130-3706726a-23d7-4731-8dff-1776077f9827.png)

