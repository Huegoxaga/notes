# Anaconda

## Introduction

- Python packages make Python capable of doing many tasks.
- Most popular packages are included in one Python distribution called Anaconda.
- It manages libraries, dependencies, and environments with Conda, instead of Python Package Index (PyPI).

## Installation

- [Click](https://www.anaconda.com/distribution/) to download Anaconda.
- Follow the instructions to install.
- Once complete, the following libraries, dependencies, and environments are ready to use.

## Jupyter NoteBook

### Introduction

- It is upgraded from `IPython`.
  - `IPython` run Python code line by line in CLI.
  - [Click](https://ipython.readthedocs.io/en/stable/index.html) to see more details.
- It is a website that can run Python code line by line. Markdown can be used to explain the codes in between.
- It has an extension as `.ipynb`.
- Blocks of codes or markdown are contained in separate cells.
- The `.ipynb` file source code is JSON data about cell objects.
- The `JupyterLab` is the newest product of the Jupyter Project.
  - [Click](https://jupyterlab.readthedocs.io/en/latest/index.html) to see details.
  - To Download JupyterLab, run command `conda install -c conda-forge jupyterlab`.
  - To Run JupyterLab, run command `jupyter lab`.

### Usage

- [Click](https://jupyter.readthedocs.io/en/latest/index.html) to see the docs for Jupyter
- Run command `jupyter notebook` to start a server and open the notebook in the browser.
- It supports LaTeX code in markdown cell, inside `$$` block.

## NumPy

### Introduction

- `NumPy` means numerical python.
- It provides high-level mathematical and numerical functions and tools.
- It utilizes numpy array which is a high-performance multidimensional data structure.
- Like any array type, Numpy arrays are a fixed size, indexed starting at 0, and contain elements of all the same type.
- Numpy arrays are defined in the class `numpy.ndarray` of the numpy package. Numpy arrays are objects of type `numpy.ndarray`.
- For any numpy arrays the dimensions are axes and the number of axes is called rank.
- [Click here](https://docs.scipy.org/doc/numpy/reference/index.html) to see `NumPy` official reference.

### Usage

#### Import the package

- add `import numpy as np` to the first line of the code.
- For most function `np.functionName(arrayName)` works the same as `arrayName.functionName()`

#### Create an array

- Create a `numpy` array of rank 1
  - `array = np.array([1,2,3,4])`
- Create a `numpy` array of rank 2
  - `array = np.array([[1,2,3,4],[5,6,7,8]])`
- Create an array of ones
- `array = np.ones((3,5))`, a `3*5` array with all elements as 1.
- Create an array of zeros
  - `array = np.zeros((2,4))`, a `2*4` array with all elements as 0.
- Create an array with random values
  - `array = np.random.random(5)`, an array with 5 random double value in range `[0,1)`.
- Create an array with certain constant
  - `array = np.full((2,2),7)`, return a `2*2` array with all elements as 7.
- Create an empty array
  - `array = np.empty()`
- Create an identity arrays
  - `np.eye()`
  - `np.identity()`
- Specify the data type for array elements upon creation
  - `array = np.full((2,2),12,dtype=np.float32)`
- Create a array from another array
  - `newArray = oldArray.copy()`
- Create an array from a `txt` file
  - `array = loadtxt(filePath)`
- Create an array that has elements in a certain range
  - `array = np.arange(start, end, step)`
  - only `end` is the required parameter.
  - when `start` is missing. It starts at 0.
  - when `step` is missing. It is 1.
- Create an array that has elements evenly spaced in a certain range
  - `array = np.linspace(start, end, numofvalues)`

#### Access the array

- Access an element of a rank 2 `numpy` array
  - `array[0,1]`, it return element value from row 0, column 1.
- `numpy` array can be printed directly.
  - `print(array)`
- Get the rank of the array.
  - `array.ndim` returns the rank.
- Get row and column number
  - `array.shape` returns array shape as `(rowNumber, columnNumber)`
- Get number of elements
  - `array.size` returns the total number of elements in the array.
- Get the data type
  - `type(array)` returns `numpy.ndarray`
- Export array to a `txt` file
  - `array.save()`

#### Modify the array

- Modify the shape of an array
  - `array.resize(newRowNum,newColumnNum)` The shape of the original array is changed.
  - `array.reshape(newRowNum,newColumnNum)` Returns a new shape, but the shape of the original array is kept intact.
  - These methods can be used to increase the rank of the array.
- Convert any array into a one-dimension array.
  - `array.ravel()` or `np.ravel(array)` returns a flattened array.
- Transpose an array
  - `np.transpose(array)` or `array.transpose()` the row and column numbers of an element are switched.

#### Doing calculations

- Arithmetic Functions
  - It works between two arrays.
  - `np.add(x,y)` or `x+y` add each element of the same location if x and y have the same shape.
    - If two arrays have different sizes, broadcasting will be performed to stretch the smaller array.
      - Broadcasting requires the arrays to have the same degree of dimension or the smaller one is a one-dimensional array.
  - It also has `subtract(x,y)`, `multiply(x,y)`, `divide(x,y)`, `remainder(x,y)` and `power(x,y)` functions.
  - Math operators `+`, `-`, `*`, `/` and `**` also works.
  - Logical comparisons are available by using `<`, `==`, and `>`. It turns an array of Booleans after comparsion each element of the same location from two arrays as result.
  - `np.dot(x,y)` return the dot product of matrix x and y.
- Elementwise Functions
  - It changes the values of all elements of one array.
  - `np.sqrt(x)` It returns a matrix of elements of `x` which all have taken the square root.
  - It also has functions `exp(s)`, `around(x,roundToNDecimal)`, `trunc(x)`, `floor(x)`, `ceil(x)`, `log(x)`.
- Array Functions
  - It works on the entire array and return a single value.
  - It has functions `sum()`, `min()`, `max()`, `cumsum(); //cumulative sum`, `mean()`, `median()`, `corrcoef()`, `std()`.
  - All functions can have `axis=1` as its parameter. This makes the function evaluate row by row, and return a list of results.
  - All functions can have `axis=0` as its parameter. This makes the function evaluate column by column, and return a list of results.
