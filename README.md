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