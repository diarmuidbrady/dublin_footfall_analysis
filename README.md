#  CA273 Assignment 3: Data Processing & Cleaning

#### List of tools I used
1. [Colab.google.com](https://colab.research.google.com/)
2. [Pandas](https://pandas.pydata.org/)
3. [Numpy](http://numpy.org/)
4. Excel
5. [Google Maps](https://www.google.com/maps/d/mp?hl=en&authuser=0&state=create)

#### Final Dataset Files
1. [The Completed Dataset](/data/processed/complete-dataset.csv)
4. [Footfall Locations](data\processed\dcc-footfall-counter-locations-14082020.csv)

## Project Summary
There were several stages in my project, I followed a basic structure of moving from one dataset to the next, however there were certain tasks which could only be completed after particular checkpoints were reached.

The project has been documented fully in the python notebook so I don't intend to regurgitate what I have done there, here, instead I would like to take another approach and discuss the main challenges I encountered and the key things I learned during the process.

This is the rough structure I followed for my project

### 1. 2010 Cleaning
2010 was by far the easiest dataset to clean and process. There were few errors encountered and these were easy to deal with

#### Challenge
There was a string in the 'Clerys' column. When trying to convert the column to dtype 'int64', I had to first correct the error by updating the whitespace to 0.

#### Key Learning Point
I learned how to manage outliers in a dataset. 999999 was the outlier encountered and I learned to replace the value as the median, as this would cause minimal skewness

### 2. 2019 Cleaning

#### Challenge
In 2019 the footfall count was recorded every quarter hour. I had to write a loop which both summed up the four quarter hour rows and then chose every fourth row on the hour mark

#### Key Learning Point
I learned to deal with missing data. The dataset's pattern of having every fourth row being the hour mark was broken due to missing data, which made it difficult to sum the rows. To resolve the problem I found the point at which the pattern broke, inspected it and sum what was left of the full hour.

### 3. 2020 Cleaning

#### Challenge
There were many null values in 2020, to replace these I used fillna(), however this can only be used on a Series.

#### Key Learning Point
I learned how to use as_type() and to_numeric() to change the dtypes. In as_type there is a parameter errors, which can be passed to either raise or ignore errors

### 4. 2019/2020 Cleaning

#### Challenge
When cleaning the column names in the 2019/2020 dataset I had to average particular columns (eg. Grafton Street). One issue is that different locations started and stopped recording footfall at different periods in time. This meant I had to extract ranges of data based on whether they were before or after a particular date.

#### Key Learning Point
In 2019/2020 there was a location at Penneys on O'Connell Street and in 2008 there was a location at Eason's on O'Connell Street, I learned the importance of domain knowledge as they two places are beside each other in real life, so they essentially recorded the same data.

### 5. 2008 Cleaning

#### Challenge
The obvious challenge I faced in 2008 was the transformation of the workbook. I spent quite a while visualizing the movement of each small column, I spent **even more** time effectively translating this into python. I had to think of different methods of merging Series and DataFrames, that being merge(), concat() and append().

#### Key Learning Point
I learned how to convert the nth day of a leap year in a date. This was particularly tricky as I tried to see how to do it in Excel first but was unsuccessful, however using a dictionary mapping the months to day ranges and some basic math I found my way.

## Overview
The real challenge I faced during this assignment was staying on track and keeping the end in mind. This has been my most enjoyable project I have worked on since I began the my data science course, unfortunately I enjoyed exploring and dwelling on different solutions too much instead of concentrating on time management, costing me precious time, resulting in an incomplete assignment. In the future, I would advise myself to work toward completion rather than perfection.
