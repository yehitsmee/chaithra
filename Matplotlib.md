/*At this point, we know how to import data by using the Pandas library. We also know how to interpret these data into arrays and manipulating them by using Numpy library. But what if we want to visualize this data? Enter matplotlib.*/
Matplotlib is easily the most used and the easiest to implement among all the libraries in python. Before we start, Disclaimer: Without knowing Numpy, understanding matplotlib is like tasting apple without biting it.
So Matplotlib can be divided into 3 sections (depending on its use and easy implementation):
1. Pylab interface (similar to MATLAB) – Pyplot tutorial.
2. Matplotlib frontend or API – artist tutorial.
3. Backends – drawing devices or renderers.

# Pyplot Tutorial

Pyplot is an object of Matplotlib which has numerous amount of command style functions, making matplotlib implementation similar to that of Matlab.
Without further delay let us start...

NOTE: the triple inverted commas(""") denote the explanation to the code. It is not necessary to read it if in case the code is understood. To those who did not understand the code, I'll be providing a step by step explanation in the triple inverted comma(""").

Lets start simple
```python
import matplotlib.pyplot as plt
fig = plt.figure()
fig.suptitle('Hello World')
fig,ax_list = plt.subplots(2,2)
```
![Insert pyplot figure schematic](https://i.stack.imgur.com/HZWkV.png)
> The first line imports matplotlib class' object pyplot. This is the object that has various functions that make the function of matplotlib similar to that of Matlab.  
> plt.figure 