/*At this point, we know how to import data by using the Pandas library. We also know how to interpret these data into arrays and manipulating them by using Numpy library. But what if we want to visualize this data? Enter matplotlib.*/
Matplotlib is easily the most used and the easiest to implement among all the libraries in python. Before we start, Disclaimer: Without knowing Numpy, understanding matplotlib is like tasting apple without biting it.
So Matplotlib can be divided into 3 sections (depending on its use and easy implementation):
1. Pylab interface (similar to MATLAB) – Pyplot tutorial.
2. Matplotlib frontend or API – artist tutorial.
3. Backends – drawing devices or renderers.

# Pyplot Tutorial

Pyplot is an object of Matplotlib which has numerous amount of command style functions, making matplotlib implementation similar to that of Matlab.
Without further delay let us start...  

> NOTE: the single bar denote the explanation to the code.   It is not necessary to read it if in case the code is understood.   To those who did not understand the code, I'll be providing a step by step explanation within the single bar.  

Lets start simple
```python
import matplotlib.pyplot as plt
fig = plt.figure()
fig.suptitle('Hello World')
fig,ax_list = plt.subplots(2,2)
plt.show()
```
![Insert pyplot figure schematic](https://i.stack.imgur.com/HZWkV.png)
> The first line imports matplotlib package's module pyplot. This is the module that has various functions that make the function of matplotlib similar to that of Matlab.    

> Instead of accessing each of the functions by writing matplotlib.pyplot.*insert-function-name*, we make it easier by using the 'as' keyword to give a smaller user-defined name such as 'plt'(convention). Hence now we can call every function as : **plt.figure()** (Instead of **matplotlib.pyplot.figure()**).  

> The figure keeps track of child Axes (Refer above Figure to understand Figure :P)   

> Axes : This is what you think of as 'a plot', it is the region of the image with the data space. The axes consists of 2(2D) or 3(3D) child axis. A given figure can have multiple Axes. 

> Axis : These are the number-line-like objects. They take care of setting the graph limits and generating the ticks (the marks on the axis) and ticklabels (strings labeling the ticks). The location of the ticks is determined by a Locator object and the ticklabel strings are formatted by a Formatter. The combination of the correct Locator and Formatter gives very fine control over the tick locations and labels.

> The second line indicates the code for plotting the figure. Since no parameters are given to the function, the figure is empty. i.e. it has no axes. The 3rd line provides the title(SuperTitle) to the figure.  

> The fourth line indicates the subplots to the figure. Subplots basically divides the figure to multiple axes. Hence it returns, 1, the Figure itself in which it has made the subplots, and 2, it returns a list of the Axes. 
Each of these axes can be further referred to and made specific changes to. Here the number of axes are 4, i.e. the (2,2) represents 2 rows and 2 columns respectively. 

> When using script in python, plt.show() shows all the active graphs in seperate windows. When in interpreter it shows the latest graph(sometimes none at all). 

**Now lets see how to use any one of these axes**
```python
import matplotlib.pyplot as plt
plt.plot(1,2)
plt.show()
```

> Dont be shocked if you didn't get any output other than the axes on this one. Infact it is exactly the way it is supposed to be because the plot is actually showing a dot. Except that the color of the dot is exactly that of the screen. Add an attribute to the plot() function. Rewrite code with :   

```python
plt.plot(1,2,'bo')
```
> The b in 'bo' indicates the color blue and the o indicates the shape of each point. Hence this code prints a blue colored 'o' shaped dot on the location 1,2(x,y).  

**To draw Lines**

```python
plt.plot([1,2,3],[3,4,5],'bo')
plt.show()
```

> We can also pass a list of x coordinates into the first argument and a list of y coordinates into the second argument to plot the points. To join these points to make a line, just dont specify the attribute 'bo'. By default the attribute is 'b-' which is a blue straight line.  

> The subplot() command specifies numrows, numcols, fignum where fignum ranges from 1 to numrows*numcols.

> Observe that the coordinates in the above figure is (1,3),(2,4),(3,5).

**Working on Multiple figure and Axes**

```python
import matplotlib.pyplot as plt


plt.figure(1)                # the first figure
plt.subplot(211)             # read as 2nd row 1st col 1st subplot.
plt.plot([1, 2, 3],'bo')
plt.subplot(212)             # the second subplot in the first figure
plt.plot([4, 5, 6])


plt.figure(2)                # a second figure
plt.plot([4, 5, 6])          # creates a subplot(111) by default

plt.figure(1)                # figure 1 current; subplot(212) still current
plt.subplot(211)             # make subplot(211) in figure1 current
plt.title('Easy as 1, 2, 3') # subplot 211 title
```
> Observe how the figure is used to address the specific plot that you want to edit. This is one of the major use of having figure.  

> When the Y axis is not specified, the coordinates are supposed to be stated as say in plt.plot([4,5,6]) gives the coordinates, (4,0) , (5,1) , (6,2).  

**Working with Labels and Axis**

> Text(in general) is an attribute of both the matplotlib.pyplot module and also the axes package.
> Observe the code below, and notice that label can be set either way. 
```python
import matplotlib.pyplot as plt
import numpy as np
fig = plt.figure(1)               #optional
ax = plt.subplot(211)
plt.title('Another test')
plt.xlabel('Label set using plt module')
ax.set_ylabel('label set using axes attribute')
ax.plot([5,4],[6,3])
plt.show()
```

 
