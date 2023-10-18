# SNL23_plots

## Description
The repository contains a Jupyter Notebook ([plotting.ipynb](/plotting.ipynb)) used to generate plots for Will Decker's poster presented at the Society for Neurobiology of Language annual meeting in Marseille, France in October, 2023. More details can be found inside the notebook. The project title is "The Spatiotemporal Architecture or Auditory Statistical Learning". More details surrounding other technical components to the project can be found [here](https://github.com/w-decker/Honors-Thesis).

## Using the notebook
This notebook makes use of a variety of Python packages and tools, including [BrainIAK](https://brainiak.org/). I recommend installing BrainIAK via conda. You can install it locally as well, but I have found it much easier to use their conda channel. Below is a simple example of how to do this. 
```bash
$ conda create -n my_env python=3.7
$ conda activate my_env
$ conda install -c brainiak -c defaults -c conda-forge brainiak
```
> Note that I have specified Python version 3.7. If you do not wish to install via conda, I would suggest reviewing their installation procedures [here](https://brainiak.org/docs/installation.html).

I have also provided _my_ environment that I created for this notebook specifically. The contents of the environment are found in [environment.yml](/environment.yml). You should make use of this if...
1. You already have BrainIAK installed
2. You wish to run the notebook yourself

To create a copy of my environment you must first clone this repository and enter it.
```bash
$ git clone https://github.com/w-decker/SNL23_plots.git
$ cd SNL_plots/
```
Next you can create a copy of my environment.
```bash
$ conda create -f environment.yml
```
> This will create an environment named "brainiak_env". Aside from _all_ the packages used in this notebook, this environment includes ipykernel, which is a necessary package for working with environments in a notebook.

If you receive errors regarding ipykernel (hopefully you will not), try the following in the terminal.
```bash
$ conda install -n brainiak_env ipykernel --update-deps --force-reinstall
```

### Where do my plots go when I render them?
If you are using this notebook to generate these plots, they will be saved in the same directory as the notebook from which you are executing the code, unless specified when the figure is rendered. For example, the following code will save your file in the same directory as your code.

```python
import matplotlib.pyplot as plt
import numpy as np

# generate sine wave
x = np.sin(np.pi*np.linspace(1, 10, 100))

plt.plot(x)
plt.title('Sin Wave')
plt.show()
plt.savefig('sinewave.png') # here is where you specify the destination of the rendered plot
```

The following code specifies a different path from the current working directory. 

```python
... # run imports and generate sine wave
import os

# get user
user = os.getlogin()

# set new directory
my_dir = f'/Users/{user}/Desktop/

# save figure to `my_dir`
plt.show()
plt.savefig(my_dir + 'sinewave.png')

```
#### Why can't you see the figures I have rendered?
I have untracked the rendered figures because it just creates clutter in the repository. The figures should be displayed inline within the notebook itself. If you wish to see the rendered figures, try running the notebook yourself or check out my poster. I usually upload copies of posters to my [website](https://w-decker.github.io/Presentations/).

## Want to contribute?
If you wish to make suggestions, please SUBMIT AN ISSUE. If you wish to contribute to the notebook, please SUBMIT A PULL REQUEST. If you wish to learn more about the project, please EMAIL [jdecke5@lsu.edu](mailto:jdecke5@lsu.edu).

## Resources
The simulated data and plots for the hidden Markov model (HMM) were adapted from tools and code provided from Chris Baldassano and BrainIAK. For a look at my adaption of the HMM code, please go [here](https://github.com/w-decker/hmm-fmri). To see the original code, check out this [blog post](http://www.chrisbaldassano.com/blog/2020/05/19/splitmerge/) from Chris Baldassano, and the [tutorials](https://brainiak.org/tutorials/12-hmm/) provided by BrainIAK. Aid in dealing with computational environments came from [Neuroimaging and Data Science](https://neuroimaging-data-science.org/root.html) a _very very_ helpful book from Ariel Rokem and Tal Yarkoni.
