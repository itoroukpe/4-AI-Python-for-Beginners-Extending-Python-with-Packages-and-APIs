## Lesson 3: Using third-party packages
In this lesson, you'll try out some third-party Python packages that let you explore and visualize data!

Loading and exploring data with pandas
One of the most popular Python third-party packages is called pandas.

It helps you with loading and exploring structured data, like the kind stored in spreadsheets and .csv files. Check out the Pandas documentation if you want to learn more!

To use the pandas package, you first need to load it:
```bash
import pandas as pd
```
import pandas as pd
🤖 Use the Chatbot:

What does "as" in the following code do?

import pandas as pd

So import pandas as pd creates a shortcut that you can use to avoid typing pandas.

Note: you'll need to use the . notation when using the function in pandas - go back to the "Using functions from a local file" lesson in this course if you need a refresher!

Next, you'll load a CSV file of used car sales prices using pandas:
```bash
data = pd.read_csv('car_data.csv')
# Dataset adapted from here https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho
data = pd.read_csv('car_data.csv')
​
print(data)
```
                         Model    Price  Year  Kilometer
0    Honda Amaze 1.2 VX i-VTEC  5050.00  2017      87150
1              Honda Brio V MT  3510.00  2014      39276
2      Honda WR-V VX MT Petrol  8199.99  2018      27963
3            Honda CR-V 2.4 AT  8600.00  2013      67000
4              Honda Brio S MT  4400.00  2016      50374
..                         ...      ...   ...        ...
153  Honda Accord 2.4 iVtec AT  1950.00  2008      57885
154       Honda City SV Diesel  7500.00  2018      75000
155               Honda City V  7300.00  2016      51834
156          Honda City SV CVT  5900.00  2015     116592
157               Honda City V  4800.00  2015      49000

[158 rows x 4 columns]
How do you show only cars that sold for more than $10,000? Let's ask the chatbot!

🤖 Use the Chatbot:

I have loaded some data using this code:
```bash
data = pd.read_csv('car_data.csv')
print(data)
```
The data looks like this when I print it:
```basg
Model Price Year Kilometer
0 Honda Amaze 1.2 VX i-VTEC 5050.00 2017 87150
1 Honda Brio V MT 3510.00 2014 39276
2 Honda WR-V VX MT Petrol 8199.99 2018 27963
3 Honda CR-V 2.4 AT 8600.00 2013 67000
4 Honda Brio S MT 4400.00 2016 50374
```
Show only the cars with a price greater than or equal to 10000.

Next, run the code the LLM wrote to filter the data by price:
```bash
# Code to show only the cars with a price >= 10000
print(data[data["Price"]>=10000])
```
                                    Model    Price  Year  Kilometer
21                           Honda City V  10600.0  2019      12382
30               Honda City ZX CVT Petrol  17000.0  2022       8530
38               Honda City ZX CVT Petrol  14500.0  2021      13000
41               Honda City VX CVT Petrol  13900.0  2022      32000
56   Honda City ZX CVT Petrol [2017-2019]  11380.0  2018       6000
63                   Honda City ZX Diesel  14900.0  2021      11000
76   Honda City VX CVT Petrol [2017-2019]  10500.0  2017      29386
78               Honda City ZX CVT Petrol  15300.0  2022       2000
79                    Honda City V Petrol  10950.0  2022       2700
88    Honda City V CVT Petrol [2017-2019]  13400.0  2021      11000
109                         Honda City VX  11990.0  2020      26497
117                  Honda City ZX Diesel  14500.0  2022       2500
121                         Honda City VX  12550.0  2021      10000
134   Honda City V CVT Petrol [2017-2019]  10400.0  2019      18000
143                Honda CR-V 2.0L 2WD AT  11300.0  2015      50000
You can also filter by other columns in the data, for example the year:
```bash
print(data[data["Year"]==2015])
```
# Show all the cars from the 2015 
```bash
print(data[data["Year"]==2015])
```
                           Model    Price  Year  Kilometer
20        Honda Mobilio S Diesel   4750.0  2015      72000
24        Honda Jazz V AT Petrol   5450.0  2015      42000
32          Honda Jazz SV Petrol   4950.0  2015      52000
36           Honda City S Diesel   6450.0  2015      64000
40           Honda City V Diesel   5250.0  2015     114635
54          Honda City VX (O) MT   5950.0  2015      72000
73                 Honda City VX   5500.0  2015      44000
93           Honda City S Diesel   5850.0  2015      61000
96       Honda Mobilio RS Diesel   6750.0  2015      48000
98          Honda City SV Diesel   5400.0  2015      76000
101            Honda City SV CVT   5900.0  2015      75258
103          Honda Jazz V Diesel   5250.0  2015      68244
123            Honda City VX CVT   6900.0  2015      59000
125    Honda Amaze 1.5 VX i-DTEC   5150.0  2015      63587
135  Honda Jazz S AT [2015-2016]   5200.0  2015      42000
143       Honda CR-V 2.0L 2WD AT  11300.0  2015      50000
156            Honda City SV CVT   5900.0  2015     116592
157                 Honda City V   4800.0  2015      49000
Pandas includes built-in tools to calculate interesting statistics, like the median selling value for the cars from 2015. Here's the code:
```bash
print(filtered_data["Price"].median())
filtered_data = data[data["Year"]==2015]
print(filtered_data["Price"].median())
```
5475.0
## Plotting data with matplotlib
This is a popular package used by data scientists and developers to visualize data. You can check out the Matplotlib documentation if you want to learn more!

To use matplotlib, you first have to import it with the following command:
```bash
# Note the .pyplot
import matplotlib.pyplot as plt
```
Don't worry about remembering this command, you can always find it by asking a chatbot or searching online. Again, the as form of the import command is being used to set up an alias - so now you can type plt instead of matplotlib.pyplot saving you lots of typing!

Let's start by using matplotlib.pyplot to plot the selling price of a car against how many miles it has driven:
```bash
plt.scatter(data["Kilometer"], data["Price"])
​
plt.title('Car Price vs. Kilometers Driven')
plt.xlabel('Kilometers Driven')
plt.ylabel('Price (in USD)')
​
plt.show()
```
Matplotlib has many settings that can help you customize your charts. You can ask a chatbot to help you write the code to modify these settings:

🤖 Use the Chatbot:

I have the following plot in matplotlib:
```bash
plt.scatter(data["Kilometer"], data["Price"])
plt.title('Car Price vs. Kilometers Driven')
plt.xlabel('Kilometers Driven')
plt.ylabel('Price (in USD)')
plt.show()
```
Please add a grid, change the scatter plot color to red, and increase the title font size.

Let's try the code the chatbot suggested:
```bash
plt.scatter(data["Kilometer"], data["Price"], color='red')
plt.title('Car Price vs. Kilometers Driven', fontsize=16)
plt.xlabel('Kilometers Driven')
plt.ylabel('Price (in USD)')
​
# Add the grid
plt.grid(True)
​
# Display the plot
plt.show()
```
Extra practice
Use the 🤖 chatbot to help you try the following exercises!

### Exercise 1
Write code to create a filtered table of all the Honda Accords in the dataset.

Hint: You can always copy and paste the code from the earlier parts of this notebook and ask the chatbot to modify it!

```bash
# WRITE YOUR CODE HERE
import pandas as pd
data = pd.read_csv('car_data.csv')

# Assuming 'data' is your DataFrame that contains the dataset
filtered_data = data[(data["Year"] == 2015) & (data["Model"].str.contains("Honda Accord"))]

# Display the filtered DataFrame
print(filtered_data)
```
### Exercise 2
Write code to display a scatter plot of sales price vs year.
```bash
# WRITE YOUR CODE HERE
​```
### Challenge exercise!
Ask the LLM to help you create a pie chart of the data showing how many cars were sold each year.

Hint: Be sure you tell the chatbot what your data variable is called! It may pick a different name by default.
```bash
# WRITE YOUR CODE HERE
```
