# pMoSS: ***p**-value* **Mo**del using the **S**ample **S**ize 

[![minimal Python version](https://img.shields.io/badge/Python%3E%3D-3.6-6666ff.svg)](https://www.anaconda.com/distribution/)
[![License](https://img.shields.io/badge/License-BSD%203--Clause--Clear-orange.svg)](https://spdx.org/licenses/BSD-3-Clause-Clear.html)

pMoSS (***p**-value* **Mo**del using the **S**ample **S**ize) is a Python code to model the *p-value* as an n-dependent function using Monte Carlo cross-validation. 

This statistical method uses the relationship between the *p-value* and the sample size to characterize the data of an experiment and decide, robustly, when the null hypothesis can be rejected.

The method uses Monte Carlo cross-validation to estimate the distribution of the *p-value* using samples of different sizes, and fits an exponential curve. When the *p-value* of a certain statistical hypothesis test is treated as a function of **n**, it is possible to get quantitative indicators of the data, such as the decay of the function or the minimum data size needed to get statistically significant differences (**n<sub>&alpha;</sub>**).

![](https://github.com/esgomezm/pMoSS/raw/master/images/pvalue_function.png)

The following figure illustrates a common output of the method. Here the cell body roundness is tested when cancer cells are treated with Taxol.

![](https://github.com/esgomezm/pMoSS/raw/master/images/cell_roundness_taxol.png)

>(Leftmost) The cell roundness distribution of control cells and cells treated at 1 nM Taxol have lower values than that of cells treated at 50 nM. (Right) The three groups were compared, the *p-values* were estimated and **p(n)** was fitted for each pair of compared groups. When Taxol at 50 nM is evaluated (blue and yellow dashed curves), **n<sub>&alpha;</sub>** is lower and the decay of **p(n)** is higher (**a** and **c** parameters  of the exponential function <img src="https://latex.codecogs.com/svg.latex?\Large&space;ae^{-cn}" title="\Large ae^{-cn}" /> ), i.e. it decreases much faster than the one corresponding comparison of control and Taxol at 1 nM (orange curve). 


## Installation

This package is tested on Python 3.6 and 3.7.
The code can be used either in a local machine or in [Google Colab](https://colab.research.google.com/notebooks/welcome.ipynb#recent=true). 

Please, note that the software is not implemented for GPU so Monte Carlo cross-validation takes quite a long time. The user can target the process by observing for a certain **n**-value, when a entire cross-validation has finished. 

### Local Machine
You need to have Python installed previously. For non-expert users, it is highly recommended to download the [Anaconda distribution](https://www.continuum.io/downloads) of Python to obtain the dependencies easily. 

Use Anaconda Navigator or Anaconda Prompt to create a new virtual environment with Python 3 and avoid any version compatibility issues:
- Create a virtual environment with [Python](https://docs.python.org/3/tutorial/venv.html) (advanced users).
- Create a virtual environment with [Anaconda Prompt](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html):
  ```shell
  conda create -n your_virtualenv python=3.6
  ```
- Create a virtual environment with [Anaconda Navigator](https://docs.anaconda.com/anaconda/navigator/tutorials/manage-environments/).

Download or [clone](https://help.github.com/articles/cloning-a-repository) this repository in your local machine.

Open Anaconda Prompt, activate your virtual environment and install all the packages specified in the requirements file:
```shell
cd to/the/directory/where/code/and/requirements.txt/are/located/
conda activate your_virtualenv
pip install -r requirements.txt
```

To run the notebook of the examples, you can install [Jupyter Notebook](https://jupyter.readthedocs.io/en/latest/index.html) either using Anaconda Navigator or Anaconda Prompt with the following command:

```shell
pip3 install --upgrade pip
pip3 install jupyter
jupyter notebook
```
In Jupyter, you have access to the directories in your local machine. Open the notebook in the examples and run the code written on it. 
### Google Colab
Open the notebook of the examples in Google Colab and add the following code lines at the beginning:

- If the code and data are located in your drive, then you need to mount it so Google Colab can access to your private files. Otherwise, you can skip this step. 

```shell
from google.colab import drive
drive.mount('/content/drive')
```
- Clone this github repository:
```shell
!git clone https://github.com/BIIG-UC3M/pMoSS.git
````
- Install the requirements:
```shell
!pip install -r /content/pMoSS/requirements.txt
````

- Modify the first line of the notebook indicating the correct path. 

  - If you clone the repository:
    ```shell
    # Load the path containing all the functions to use pMoSS
    from sys import path
    path.append('/content/pMoSS/pMoSS/')
    ````
  - If you have the entire code in your drive:
    ```shell
    # Load the path containing all the functions to use pMoSS
    from sys import path
    path.append('/content/drive/My Drive/the_path_in_your_drive/pMoSS/pMoSS/')
    ````
You are ready to run the code in the notebook!

## System requirements
Operating systems.
* Windows
* Mac OSX
* Linux

Python version and packages:
* Python 3.6 (or newer)
* numpy
* scipy>=1.1.0
* pandas
* matplotlib
* xlrd>=1.0.0
* seaborn
* statsmodels>=0.9.0
* glob
* shutil
* os

## Examples
You can find examples of data analysis in the example folder. A Google Colab notebook is provided for a quick test.

## Feedback and contributions
- All kind of feedback is welcome. Specially if it supports the use of the code and a better understanding on how to work with it.
- Controbutions are also welcome. Please, create a new pull request on a new development branch to add new features, correct bugs or make changes in the code.
- Please, if possible, use GitHub [Issues](https://github.com/esgomezm/pMoSS/issues) to report any bug or ask questions.


## Conditions of use
pMoSS is an open-source software (OSS) under the BSD 2-Clause License. All the resources provided here are freely available for non-commercial and research purposes. Their use for any other purpose is generally possible, but solely with the explicit permission of the authors. You are expected to include adequate references whenever you present or publish results that are based on the resources provided.

## References
E. Gómez-de-Mariscal, A. Sneider, H. Jayatilaka, J. M. Phillip, D. Wirtz and A. Muñoz-Barrutia, "Confronting p-hacking: addressing p-value dependence on sample size." BiorXiv, 2019.
