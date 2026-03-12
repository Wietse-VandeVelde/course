# Machine Learning project steps  

# Import relevant libraries  

![libraries image](my_summary_images/libraries.PNG)

# Look at the big picture  

## Frame the problem  

- Ask what the business objective is!
- This determines  
  - which algorithms to select
  - which performance measure you will use
  - how much effort you will spend tweaking it  

Before you continue, ask yourself:  

- What are the instances?
- Which techniques to use?
  - reinforcement learning
  - (un)supervised learning
  - classification/regression
  - batch/online learning

## Select a performance measure  

- Root Mean Squared Error (RMSE)
  - this is the prefered method for most regression problems
- Mean Absolute Error (MAE)
  - this can be better when there are many outliers because RMSE punishes larger errors
- Mean Absolute Percentage Error (MAPE)
  - this tells you how far predictions are on average

# Collect the data

## Download the data
`pd.read_csv('path/to/csvfile')`  
Other file formats and even download through url is possible.  

## Take a quick look at the data structure

`df.head()`  
`df.tail()`  
Through this quick look you can see if the data has been correctly fetched and opened.  

`df.info()`  
Shows you the amount of rows and columns. The names of the columns and their datatype. And the non-null count of each column. Can also be called on a column.  

`df.describe()`  
Shows you a summary of the numerical attributes. Can also be called on a column. Call it on a categorical column will show a different summary.  

`df['column_name'].value_counts`  
Shows you how many time each value is present in the column. Useful for categorical columns.  

## Plot a histogram for each numerical attribute  

`df.hist(bins=v1, figsize=(v2, v3))`  
`plt.show()`  
You can make some observations from these.  

## Create a test set  

`np.random.seed(42)`  
If you don't use _np.random.seed(42)_ and you run the program again, it will generate a different test set! Over time, you (or your Machine Learning
algorithms) will get to see the whole dataset, which is what you want to avoid.  

`train_set, test_set = train_test_split(df, test_size=0.2, random_state=42)`  

- Random sampling is fine if your dataset is large enough (relative to the number of attributes)
- But you run the risk of introducing a significant sampling bias
- Suppose the median income is a very important attribute to predict median housing prices.
- Then make sure that you have +/- the same distribution in your test set as in the whole dataset.
- This is called __stratified sampling__ which is especially useful if you a have skew dataset.
- Since the median income is a continuous numerical attribute, you first need to create an income category attribute.

![1](my_summary_images/stratified_sampling_1.PNG)  
![2](my_summary_images/stratified_sampling_2.PNG)  
![3](my_summary_images/stratified_sampling_3.PNG)  

# Discover and visualize the data to gain insights  

