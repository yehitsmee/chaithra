At this point, we know how to import data by using the Pandas library. We also know how to interpret these data into arrays and manipulating them by using Numpy library. But what if we want to visualize this data? Enter matplotlib.  
Matplotlib is easily the most used and the easiest to implement among all the libraries in python. Before we start, Disclaimer: Without knowing Numpy, understanding matplotlib is like tasting apple without biting it.
So Matplotlib can be divided into 3 sections (depending on its use and easy implementation):  

1. Pylab interface (similar to MATLAB) – Pyplot tutorial.
2. Matplotlib frontend or API – artist tutorial.
3. Backends – drawing devices or renderers.
This wiki will be basically covering Pyplot. I would encourage reading up on the artist and the renderers, but its not necessary. The way most of us learnt python was by implementing other stuffs and learning these libraries on the go.   

TIP: Get well versed and used to reading documentations. There are really good Documentations provided(like for this library) while others simply suck. Anyway, this doc should at the least get you started.   

Refer here for installation tutorial:  
https://matplotlib.org/users/installing.html  
Youtube:  
https://www.youtube.com/watch?v=-llHYUMH9Dg  

Lastly this video playlist is amazing for matplotlib, covers more than enough stuffs:  
https://www.youtube.com/playlist?list=PLQVvvaa0QuDfefDfXb9Yf0la1fPDKluPF  

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

## Using individual axes

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

## To make Coordinates and join them

```python
plt.plot([1,2,3],[3,4,5],'bo')
plt.show()
```

> We can also pass a list of x coordinates into the first argument and a list of y coordinates into the second argument to plot the points. To join these points to make a line, just dont specify the attribute 'bo'. By default the attribute is 'b-' which is a blue straight line.  

> The subplot() command specifies numrows, numcols, fignum where fignum ranges from 1 to numrows*numcols.

> Observe that the coordinates in the above figure is (1,3),(2,4),(3,5).

## Working on Multiple figure and Axes(Subplots)

```python
import matplotlib.pyplot as plt


plt.figure(1)                # the first figure
plt.subplot(211)             # read as 2nd row 1st col 1st subplot
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
  
> plt.subplot(211) can also be written as plt.subplot(2,1,1) which is plt.subplot(nrow,ncol,index) where the index is the position of the figure from left to right.
**NOTE**: all the values in subplot must be < than 10.   

**Alternately**
```python
import matplotlib.pyplot as plt

fig,ax = plt.subplots(2)
ax[0].plot([1, 2, 3],'bo')
ax[1].plot([4, 5, 6])
plt.figure(2)
plt.plot([2,3])
ax[1].set_title('Easy as 123')
```
> The first approach is a Matlab style interface and the second is an object oriented interface.  

> In subplots its important to understand the parameters. If the subplot parameters say (2,1,1) then it means that within a 2x1 grid create subplot 1. Hence a 2x1 grid can provide a maximum of 2 subplots and not more. Thus, if the parameter is given as (2,1,4) it will give an error although a parameter like (2,3,4) will be correct. Refer to the figure below :
![Different subplot and indexes](https://i.stack.imgur.com/AEGXG.png)   

 **To have 1 column of same subplot:**

![Column overlap](https://i.stack.imgur.com/JKbnc.gif)
 
 **To have a row of same subplot:**

![Row overlap](https://i.stack.imgur.com/hH2vj.gif)

## Working with Labels and Axis

> Text(in general) is an attribute of both the matplotlib.pyplot module and also the axes package.
> Observe the code below, and notice that label can be set either way. 
```python
import matplotlib.pyplot as plt
fig = plt.figure(1)               #optional
ax = plt.subplot(211)
plt.title('Another test')
plt.axis([0,6,0,20])
plt.xlabel('Label set using plt module')
ax.set_ylabel('label set using axes attribute')
ax.plot([5,4],[6,3])
plt.show()
```
> **plt.axis([0,6,0,20])**  -  This line gives the parameters to the axis, that is the parameters are given as a list that contains 4 values - xmin,xmax,ymin,ymax.  

> As you will see in the output, the values are incremental and will be according to the best fit of the line. If you want to make it incremental specific to you then use the following attribute: 

**plt.xtick([0.5,1.0,1.5,2.0,3.0])** - this will label the number line in x axis exactly the way it is given in the list.  

 ## Using Numpy with matplotlib

We can also use numpy arrays instead of List. Infact this is more favorable as numpy arrays allow more implementation than lists.

```python
fig = plt.figure()
ax = plt.axes()
x = np.linspace(1,10,1000)
ax.plot(x,np.sin(x))
ax.plot(x,np.cos(x))             #Can have multiple lines in the same axes.
plt.show()
```
The above should output a sine curve.
As said earlier, this can also be done as:
```python
x = np.linspace(1,10,1000)
plt.plot(x,np.sin(x))
plt.plot(x,np.cos(x))            #Can have multiple lines in the same axes
plt.show()
```
We can further integrate Linestyles and colors by doing so: 
```python
#for Linestyle
plt.plot(x,np.sin(x),linestyle = '-')   #equivalent to : plt.plot(x,np.sin(x),linestyle = solid)
#for color:
plt.plot(x,np.cos(x),color = 'blue')   #can also mention hexcodes instead
#for both:
plt.plot(x,np.sin(x+1),'-g')
```
We can also adjust the x and y axis limits as such:

```python
plt.plot(x, np.sin(x))
plt.xlim(-1, 11)
plt.ylim(-1.5, 1.5);
#alternatively
plt.axis(-1,11,-1.5,1.5)
```
We can also fit the graph to the curve by using **plt.axis('tight')** or also make the aspect ratio equal by: **plt.axis('equal').  

To Construct **Legends**:  
Use plt.plot() attribute as : plt.plot(x,np.sin(x),'-g',label = 'sinx')
And to show the legend use , plt.legend()

```python
plt.plot(x, np.sin(x), '-g', label='sin(x)')
plt.plot(x, np.cos(x), ':b', label='cos(x)')
plt.axis('equal')

plt.legend();
```
While most plt functions translate directly to ax methods (such as plt.plot() → ax.plot(), plt.legend() → ax.legend(), etc.), this is not the case for all commands. In particular, functions to set limits, labels, and titles are slightly modified. For transitioning between MATLAB-style functions and object-oriented methods, make the following changes:

    plt.xlabel() → ax.set_xlabel()
    plt.ylabel() → ax.set_ylabel()
    plt.xlim() → ax.set_xlim()
    plt.ylim() → ax.set_ylim()
    plt.title() → ax.set_title()

In the object-oriented interface to plotting, rather than calling these functions individually, it is often more convenient to use the ax.set() method to set all these properties at once:

```python
ax = plt.axes()
ax.plot(x, np.sin(x))
ax.set(xlim=(0, 10), ylim=(-2, 2),
       xlabel='x', ylabel='sin(x)',
       title='A Simple Plot');
```
## SPINES

![Spines explanation image](https://matplotlib.org/_images/spines_demo.png)

Spines are the lines connecting the axis tick marks and noting the boundaries of the data area.   
Spines are like the boundaries that the cells in Excel sheet. We can change those boundaries to cover a certain area, no area ,etc.  

We will be understanding spines by implementing the above image in python.   
```python
"""
This demo compares:
    - normal axes, with spines on all four sides;
    - an axes with spines only on the left and bottom;
    - an axes using custom bounds to limit the extent of the spine.
"""
import numpy as np
import matplotlib.pyplot as plt


x = np.linspace(0, 2 * np.pi, 100)
y = 2 * np.sin(x)

fig, ax= plt.subplots(nrows=3)

ax[0].plot(x, y)
ax[0].set_title('normal spines')

ax[1].plot(x, y)
ax[1].set_title('bottom-left spines')

# Hide the right and top spines
ax[1].spines['right'].set_visible(False)
ax1.spines['top'].set_visible(False)
# Only show ticks on the left and bottom spines
ax[1].yaxis.set_ticks_position('left')
ax[1].xaxis.set_ticks_position('bottom')

ax2.plot(x, y)

# Only draw spine between the y-ticks
ax[2].spines['left'].set_bounds(-1, 1)
# Hide the right and top spines
ax[2].spines['right'].set_visible(False)
ax[2].spines['top'].set_visible(False)
# Only show ticks on the left and bottom spines
ax[2].yaxis.set_ticks_position('left')
ax[2].xaxis.set_ticks_position('bottom')

# Tweak spacing between subplots to prevent labels from overlapping
plt.subplots_adjust(hspace=0.5)
plt.show()
```
There are lots of other things that this library could do, it wouldn't be possible to have it all written down here. Refer to the official docs as and when needed. The best way to learn Python is to implement it along the way. Follow the references given below:

## REFERENCES:
**Official DOCS:**
https://matplotlib.org/tutorials/introductory/usage.html#sphx-glr-tutorials-introductory-usage-py
https://matplotlib.org/tutorials/introductory/pyplot.html#sphx-glr-tutorials-introductory-pyplot-py
https://matplotlib.org/tutorials/intermediate/artists.html#sphx-glr-tutorials-intermediate-artists-py
https://matplotlib.org/tutorials/text/text_intro.html#sphx-glr-tutorials-text-text-intro-py
https://matplotlib.org/tutorials/text/text_props.html#sphx-glr-tutorials-text-text-props-py
**Recommended Docs:**
https://realpython.com/python-matplotlib-guide/
**Suggested Books for Data Science**
http://shop.oreilly.com/product/0636920034919.do
Free online version:
https://jakevdp.github.io/PythonDataScienceHandbook/04.00-introduction-to-matplotlib.html


