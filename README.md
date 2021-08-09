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

