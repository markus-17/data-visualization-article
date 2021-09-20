### Stuff this article aims to cover

* What is **matplotlib**?
* How to make simple **line** plots?
* How to make simple **scatter** plots?
* Error bars
* Contour plots
* Histograms, Binning and Density
* How to use **seaborn** to make better looking plots?


# What is matplotlib?

**Matplotlib** is a multiplatform data visualization library built on **NumPy** arrays, and designed to work with the broader **SciPy** stack. One of Matplotlib’s most important features is its ability to play well with many operating systems and graphics backends. Matplotlib supports dozens of backends and output types, which means you can count on it to work regardless of which operating system you are using or which output format you wish.

Just as we use the **np** shorthand for **NumPy** and the **pd** shorthand for **Pandas**, these are some standard shorthands for Matplotlib imports:

```py
import matplotlib as mpl 
import matplotlib.pyplot as plt
```

A potentially confusing feature of Matplotlib is its dual interfaces:

* the MATLAB-style state-based interface
* the object oriented interface

## MATLAB-style interface

Matplotlib was originally written as a **Python** alternative for **MATLAB** users, and much of its syntax reflects that fact. The MATLAB-style tools are contained in the pyplot (**plt**) interface.

```py
plt.figure(dpi=150) # create a plot figure

x = np.linspace(0, 10)

# create the first of two panels and set current axis
plt.subplot(2, 1, 1) # (rows, columns, panel number)
plt.plot(x, np.sin(x))

# create the second panel and set current axis
plt.subplot(2, 1, 2)
plt.plot(x, np.cos(x))
```

![image1](./images/image1.png)

## Object oriented interface

The object-oriented interface is available for more complicated situations, and for when you want more control over your figure. Rather than depending on some notion of an “active” figure or axes, in the object-oriented interface the plotting functions are methods of explicit **Figure** and **Axes** objects.

```py
fig, ax = plt.subplots(2, dpi=150)

# Call plot() method on the appropriate object
ax[0].plot(x, np.sin(x))
ax[1].plot(x, np.cos(x))
```

![image2](./images/image2.png)

For more simple plots, the choice of which style to use is largely a matter of preference, but the object-oriented approach can become a necessity as plots become more complicated.

# How to make simple line plots?

Perhaps the simplest of all plots is the visualization of a single function y = f(x).

In the following example we demonstrate how a figure and axes can be created using **plt.figure** and **plt.axes** respectively. Once we have created an axes, we can use the **ax.plot** (or the **plt.plot**) function to plot some data. Since we want to create a single figure with multiple lines, we can simply call the **plt.plot** function multiple times. **plt.plot** function takes additional arguments (that are optional) that can be used to specify the **color**, **label**, **linestyle** and others. If no color is specified, Matplotlib will automatically cycle through a set of default colors for multiple lines. Matplotlib does a decent job of choosing default axes limits for your plot, but sometimes it’s nice to have finer control. The most basic way to adjust axis limits is to use the **plt.xlim()** and **plt.ylim()** methods. We can also set the title and axis label using **plt.title**, **plt.xlabel**, **plt.ylabel**. And finally, when multiple lines are being shown within a single axes, it can be useful to create a plot legend that labels each line type. It is easiest to specify the label of each line using the **label** keyword of the **plot** function and then call **plt.legend**.

```py
# We can use the plt.style directive to choose appropriate
# aesthetic styles for our figures
plt.style.use('seaborn-whitegrid') 

fig = plt.figure(dpi=150)
ax = plt.axes()

plt.plot(x, np.sin(x), color='red', label='sin(x)')
plt.plot(x, np.cos(x), color='green', linestyle='dotted', label='cos(x)')

plt.xlim([-2, 12])
plt.ylim([-1.25, 1.25])

plt.title('The sine and the cosine function')
plt.xlabel('x')
plt.ylabel('y')

plt.legend()
```

![image3](./images/image3.png)

# How to make simple scatter plots?

