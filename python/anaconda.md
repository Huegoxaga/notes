# Anaconda

## Introduction

- Python packages make Python capable of doing many tasks.
- Most popular packages are included in one Python distribution called Anaconda.
- It manages libraries, dependencies, and environments with Conda, instead of Python Package Index (PyPI).

## Installation

- [Click](https://www.anaconda.com/distribution/) to download Anaconda.
- Follow the instructions to install.
- Once complete, the following libraries, dependencies, and environments are ready to use.

## Conda

- It is the package manager that aimed to replace `pip`.
- It is a virtual environment tool that can replace `virtualenv`.
- [Click here](https://docs.conda.io/projects/conda/en/latest/commands.html) for complete command reference.
- Environments separate projects to run with certain packages and python version installed in this environment.
  - The `base` environment is the default environment that has up-to-date python and all anaconda packages installed inside.
- Packages and Environments can be controlled using a GUI tool called Anaconda Navigator.
- If conda cannot find a certain package use `pip` to install.
  - It is better to create a conda environment to isolate any changes pip makes
  - the packages installed by `pip` won't be managed by the Conda package manager, they will still be managed by the Anaconda environment
    - Any packaged installed by `pip` can be found using `conda list`. However, conda won't track all changes made by `pip`.
    - conda env will export or create environments based on a file with conda and pip requirements.
- Remember to restart all terminals when installation or changes are made.

### Commands

- `anaconda-navigator` start an instance of the Anaconda Navigator
- `conda list` list installed packages and versions installed in active environment
- `conda list --revisions` List the history of each change to the current environment
- `conda info` Verify conda is installed, check version number
- `conda update conda` Update conda to the current version
- `conda install <packagename>` Install a package included in Anaconda
  - `conda install <packagename> --file filename.txt` install packages base on text file info.
- `conda update <packagename>` Update any installed program
- `conda create --name py35 python=3.5`Create a new environment named py35, install Python 3.5
  - `conda create --name bio-env <packagenametoinstall>` all in one command for creating env and instal packages.
  - Versions can be specified as the following ways.
  - `numpy=1.11` all its subversion are included like `1.11.0` and `1.11.1`
  - `numpy==1.11` exact match `1.11.0`
  - `"numpy>=1.11"`
  - `"numpy=1.11.1|1.11.3"`
  - `"numpy>=1.8,<2"`
- `source activate py35` Activate the new environment to use it.
- `conda env list` list all environment, activated one is shown with `*`
- `conda create --clone <envname> --name <newname>`Make exact copy of an environment
- `conda install --revision 2` Restore environment to a previous revision
- `conda list --explicit > bio-env.txt` Save environment to a text file
- `conda env remove --name bio-env` Delete an environment and everything in it
- `conda deactivate` Deactivate the current environment
- `conda env create --file bio-env.txt` Create environment from a text file
- `conda search <keyword>` search packages
- `conda install <packagename>` Install a new package (Jupyter Notebook) in the active environment
  - `conda install python=3.5.0` Install a certain version of python or packages for the env.
- `conda install --name <env-name> <packagename>` Install a new package in a different environment.
- `conda update <packagename>` Update a package in the current environment
- `conda remove --name bio-env toolz boltons` Remove one or more packages (toolz, boltons) from a specific environment (bio-env)
- `which -a python` Show the locations of all versions of Python that are currently in the path
  - The first version of Python in the list will be executed.

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
- Run command `jupyter notebook` in the project folder to start a server and open the notebook in the browser.
- It supports LaTeX code in markdown cell, inside `$$` block.
- `Shift + Enter` to run code block in the cell.

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

## Pandas

### Introduction

- It is used to process data in tables.
- Dataframe stores data in rows and columns of a table.
- Dataframe is a dictionary structure that has column names as the key. All data for one column is stored in a list from top to bottom as value for the key.
- A column of data is of type series. It has a 1-D list structure.
  - Dataframe is a container for multiple series.
- [Click](https://pandas.pydata.org/docs/reference/index.html) to see the completed documentation for more details.
- run `pip install pandas` to install it separately.
- By default many method itself in `pandas` will not change the data it stores. A `inplace` parameter is required to set `True` to make it happen. This is great to run without `inplace` first to see if it gives expected results then add the parameter to confirm changes.

### Usage

- `import pandas as pd`
- `df = pd.read_csv('filePath.csv')` load a csv file.
  - `df = pd.read_csv('filePath.csv', index_col='colName')` load a csv file, and using a column as its index.
- `df.shape` return the `(row, column)` of the dataframe.
- run `df` to print out data frame in Jupyter directly
- `df.info()` returns shape column name and column data type about the dataframe.
- `pd.set_option('display.max_columns', 10)` display a max of 10 columns when print.
- `pd.set_option('display.max_rows', 10)` display a max of 10 rows when print.
- `df.head(10)` show the first 10 rows of data.
  - If no parameter entered it will show the first 5 rows.
- `df.tail(10)` show the last 10 rows of data
  - If no parameter entered it will show the last 5 rows.
- `df = pd.DataFrame(data)` convert dictionary data into dataframe
- `df['columnName']` print all data under one column plus its data type(return a series).
  - `df.columnName` dot notation also works.
  - `df[['columnNameA','columnNameB]]` returns al list of columns(a filtered dataframe)
  - `df['columnName']= df['columnName'].str.lower()` change all data in one column in lowercase.
  - `df['columnA'] + '@' + df['columnB']` edit and combine data from two column and create a new series.
  - `df['NewCol'] = series` create a new column called `NewCol` with data from `series`
  - `df[['ColA','ColB']]=df['Col'].str.split(' ', expand=True)` split one col into two new column.
- `df.columns` show info about all columns.
  - `df.columns = ['ColName1', 'ColName2', 'ColName3']` rename all column field names.
  - `df.columns = [x.upper() for x in df.columns]` change all field name to uppercase.
  - `df.columns = df.columns.str.replace(' ', '_')` change all space in the column name to `_`.
- `df.rename(columns={'ColNameA': 'ColNameB', 'NewColNameA': 'NewColNameB'}, inplace=True)` rename certain column field names.
- `df.drop(columns=['ColA', 'ColB'], inplace=True)` delete certain columns.
- `df.iloc[0]` `iloc` return data based on integer location. In the example returns the first row .
  - `df.iloc[rowIndex, colIndex]` return data from certain row and column.
  - `df.iloc[[0,1]]` returns the first and second row as dataframe.
  - `df.iloc[0:5]` returns the first 5 rows using slicing.
  - `df.iloc[[0,1],1]` return data from the first and second row, and second coloumn.
- `df.loc[[0,1],'columnName']` `loc` similar to `iloc` but it return data based on label and the default index label.
  - slicing also works with label, ``df.loc[[0,1],'columnNameA':'columnNameB']`
  - `df.loc[2] = ['newdata1', 'newdata2', 'newdata3']` update the third row with new data.
  - `df.loc[2, ['Col2', 'Col3']] = ['newdata2', 'newdata3']` update the third row's data in column2 and column3.
  - `df.loc[2, 'Col2'] = 'newdata2'` or `df.at[2, 'Col2'] = 'newdata2'` update a single value.
- `series.value_counts()` count unique values in the series.
- `df.set_index('columnName')` set a column as the index, then and print
  - This method does not change the original dataframe. To replace the original dataframe use, `df.set_index('columnName' inplace=True)`.
  - Once the customized index is set the default integer index will not be available for the `loc` method.
- `df.index` review index info.
- `df.reset_index(inplace=True)` reset the index to default.
- `df.sort_index()` sort index in descending order.
  - `df.sort_index(ascending=False)` sort index in ascending order.
  - `df.sort_index(inplace=True)` sort index in descending order and replace the original dataframe.
- `ft = (df['colName'] == 'Value')` It return a series of boolean values. True means a match is found. False means the column value and the filter value does not match.
  - filter is a key word that can not be used.
  - To access all the match values, run `df[ft]`
  - `-ft` will negate the filter result.
  - use `==`, `>`,`>=`,`<=`, `<` for the expression.
  - Combine expression with and(`&`), or(`|`) to make the filter powerful.
  - `df.loc[ft]` also works, It column can also be specified. Ex: `df.loc[ft,'colA']`
  - `ft = df['colName'].isin(listValue)`, it can be used to check membership relationship for a list of values.
  - `ft = df['ColName'].str.contains('value', na=False)` find records contain `value` in the string, and ignore all cells does not have value.
- `df['col'].apply(x)` `x` is a function or property that will be passed and run on all data in the column.
  - `df['col'] = df['col'].apply(x)` updata the data with newly calculated values.
  - `x` can be a lambda function. Ex, `df['col'].apply(lambda x: x.lower())`
- `df.apply(x)` apply `x` function on each searies object on each columns vertically.
  - `df.apply(x, axis='columns')` apply `x` function on each searies object on each rows horizontally.
- `df.applymap(x)` apply `x` function on each data object in the dataframe.
- `df['col'] = df['col'].map({'data1': 'newdata1', 'data2': 'newdata2'})` replace certain data in the column, unchanged data will be set to NaN.
- `df['col'] = df['col'].replace({'data1': 'newdata1', 'data2': 'newdata2'})` replace certain data in the column, unchanged data will be left unchanged.
- `df.sort_values(by='col', ascending=False)` Sort data by certain colum in descending order.
  - `df.sort_values(by=['colA', 'colB'], ascending=False)` order by two columns.
  - `df.sort_values(by=['last', 'first'], ascending=[False, True])` order by two columns in different order.
  - `df['col'].sort_values()` sort series from one column.
- `df.sort_index()` sort by index.
- `df['col'].nlargest(10)` show the 10 largest data of a column as series.
- `df.nsmallest(10, 'col')` show the 10 smalleset data of a column as series.

## Matplotlib

### Introduction

- It is used to plot graphs.
- [Click](https://matplotlib.org/contents.html#) to see the completed documentation for more details.

### pyplot

- `from matplotlib import pyplot as plt`
- `plt.plot(listofX, listofY)` plot a line, run this method multiple times to draw multiple lines.
  - `plt.plot(listofX, listofY, label='line legend')` add a legend to the line.
  - `plt.plot(listofX, listofY, color='#3b3b3b', linewidth=2,linestyle='--' label='line legend')` or `plt.plot(listofX, listofY, 'formatstring',label='line legend')` to add format to the line, see details about the characters [here](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.plot.html#matplotlib.pyplot.plot)
- `plt.bar(listofX, listofY, label='bar legend')` draw a bar chart.
  - Use numpy to off set the x-value to display multiple groups of data using bar chart.`plt.bar(np.arange(len(x_datalist))+0.25, y_datalist, width=0.25, color="#ebebeb", label="labelName")`
- `plt.barh(x_data, y_data)` draw a horizontal bar chart.
- `plt.xticks(ticks=np.arange(len(x_datalist)), labels=x_datalist)` display the corrent x-axis label.
- `plt.pie(integer_list)` plot a pie chart. The percentage is auto calculates
  - `plt.pie(integer_list, labels=label_list)` add labels.
  - `plt.pie(integer_list, labels=label_list, wedgeprops={'edgecolor':'black'})` add edge.
  - `plt.pie(integer_list, explode=explodefactor_list)` For the factor, `0` mean no explode. `0.1` should be good enough.
  - `plt.pie(integer_list, shadow=True)` show a shadow
  - `plt.pie(integer_list, startangle=90)` rotate the pie chart
  - `plt.pie(integer_list, autopct='%1.1f%%')` show percentage data in the pie chart
  - `plt.pie(integer_list, color= color List )` add labels.
- `plt.stackplot(x_data_list,list_of_list)` or `plt.stackplot(x_data_list,list1,list2,list3)` draw a stackplot.
  - It also has labels and colors parameters.
- `plt.fill_between(x_data_list,y_data_list,alpha=0.2)` fill the plot in color with 0.2 opacity from the bottom.
  - `plt.fill_between(x_data_list,y_data_list,y_axis_fill,alpha=0.2)` fill in color above and below the `y_axis_fill` line.
  - add `where(y_data_list<y_axis), interpolate=True` to fill below certain line.
  - The `y-axis` data can also be a list.
  - add `label='label text'` to add legend for fill.
- `plt.hist(data_list, bin=5, edgecolor='black')` divide a list of data into 5 category with edgecolor.
  - the range of bin can be set by passing into a list of boundaries.
  - add `log=True` draw data in the logorithmic scale(y-axis will be 10^n).
- `plt.axcline(y, label="text")` add a vertical line in the graph.
- `plt.xlabel('XAxisLabel')`
- `plt.ylabel('YAxisLabel')`
- `plt.title('Graph Title')`
- `plt.legend()` add legend base on labels automatically
  - `plt.legend(['firstLineLegend','firstLineLegend'])` set legend text.
  - `plt.legend(loc='upper left')` or `plt.legend(loc=(percent_from_left, percent_from_bottom))` set the legend location.
- `plt.tight_layout()` set a tight padding.
- `plt.grid(True)` show grid
- `print(plt.style.available)` show the styles available
- `plt.style.use('stylename')` set a style
- `plt.skcd()` set a comic style
- `plt.show()` show the graph
- `plt.savefig('filename.png')` save the file in the working directory.

## BeautifulSoup

### Introduction

- It is used to process strings containing `html` source code.
- `from bs4 import BeautifulSoup`

### Usage

- `soup = BeautifulSoup(html, features='lxml')` load the source code string into a soup object.
- `soup.tagName` access all the content in between certain tag. Ex, `soup.p` print all html source code start with `<p>` and end with `</p>`.
- `soup.find_all('tagName')` return a list of matched soup objects.
- `soup['attribute']` access certain attribute of a tag. Ex, `soup['href']`.
- `soup.find_all('tagName', {"attribute": "value"})` return a list of tags with certain attribute value.
  - Attribute value can be replaced by a complied regular expression patterm. Ex, `soup.find_all('a', {'href': re.compile('https://example.*')})`
- `soup.get_text()` get the text inside the tag.
- `soup.find('ul', {"class": "className"})` `find` method return the one result.

## Celery

### Introduction

- It’s a task queue with focus on real-time processing, while also supporting task scheduling.
- It is not included in the anaconda default package, and need to be installed using command `conda install celery`.

### Basic Usage

1. Celery requires a broker to store task list in a queue. There are three options, follow one of the link to install:
   - RabbitMQ - [click](http://docs.celeryproject.org/en/latest/getting-started/brokers/rabbitmq.html#broker-rabbitmq) to see installation & configuration instruction.
   - Redis - [click](http://docs.celeryproject.org/en/latest/getting-started/brokers/redis.html#broker-redis) to see installation & configuration instruction.
     - run `pip install -U "celery[redis]"` to install Celery and Redis as a bundle.
     - For Django app add `BROKER_URL = 'redis://localhost:6379/0'` and `BROKER_TRANSFER = 'redis'` in `settings.py`.
   - Amazon SQS - [click](http://docs.celeryproject.org/en/latest/getting-started/brokers/sqs.html#broker-sqs) to see installation & configuration instruction.
2. Defines the task in `tasks.py`
   ```py
   from celery import Celery
   app = Celery('tasks', broker='pyamqp://guest@localhost//')
   @app.task
   def add(x, y):
     return x + y
   ```
3. Run the Celery server by running command `celery -A <projectName> worker --loglevel=info`.
4. Call the task
   ```py
   from tasks import add
   >>> add.delay(4, 4)
   ```
5. Setup and view the result
   1. add the `backend` argument to Celery, using a selected backend storage method from [here](http://docs.celeryproject.org/en/latest/getting-started/first-steps-with-celery.html#keeping-results)
   2. Access result using the following ways
   ```py
   result = add.delay(4, 4)
   result.ready() #return true if it is done.
   result.get(timeout=1) # get result after a certain duration.
   result.get(propagate=False) # preventing a exception is reraised when calling get() after an error.
   result.traceback #  access to the original traceback after a exception is raised.
   # Remember to call either get() or forget() to release the memory
   result.forget()
   ```
6. Do additional settings
   - To change a certain settings `app.conf.task_serializer = 'json'`
   - To change multiple settings:
     ```py
     app.conf.update(
     task_serializer='json',
     accept_content=['json'],  # Ignore other content
     result_serializer='json',
     timezone='Europe/Oslo',
     enable_utc=True,
     )
     ```
   - To change settings from a config file, use `app.config_from_object('celeryconfig')`, An example config file named `celeryconfig.py` is shown as follows:
     ```py
     broker_url = 'pyamqp://'
     result_backend = 'rpc://'
     task_serializer = 'json'
     result_serializer = 'json'
     accept_content = ['json']
     timezone = 'Europe/Oslo'
     enable_utc = True
     ```

### Work with Django

1. Add the Celery instance definition at `proj/proj/celery.py`
   ```py
   from __future__ import absolute_import, unicode_literals
   import os
   from celery import Celery
   # set the default Django settings module for the 'celery' program.
   os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'proj.settings')
   app = Celery('proj')
   # Using a string here means the worker doesn't have to serialize
   # the configuration object to child processes.
   # - namespace='CELERY' means all celery-related configuration keys
   #   should have a `CELERY_` prefix.
   app.config_from_object('django.conf:settings', namespace='CELERY')
   # Load task modules from all registered Django app configs.
   app.autodiscover_tasks()
   @app.task(bind=True)
   def debug_task(self):
       print('Request: {0!r}'.format(self.request))
   ```
2. Let celery start in the `proj/proj/__init__.py` when django starts.
   ```py
   from __future__ import absolute_import, unicode_literals
   # This will make sure the app is always imported when
   # Django starts so that shared_task will use this app.
   from .celery import app as celery_app
   __all__ = ('celery_app',)
   ```
3. Write tasks in the `tasks.py` in app folders
   ```py
   # Create your tasks here
   from __future__ import absolute_import, unicode_literals
   from celery import shared_task
   from demoapp.models import Widget
   @shared_task
   def add(x, y):
       return x + y
   @shared_task
   def mul(x, y):
       return x * y
   @shared_task
   def xsum(numbers):
       return sum(numbers)
   @shared_task
   def count_widgets():
       return Widget.objects.count()
   @shared_task
   def rename_widget(widget_id, name):
       w = Widget.objects.get(id=widget_id)
       w.name = name
       w.save()
   ```

### Celery Beat

- This is a celery extension that stores the schedule in the Django database, and presents a convenient admin interface to manage periodic tasks at runtime.
- Setup steps:
  1. Use pip to install the package, `pip install django-celery-beat`
  2. Add the `django_celery_beat` module to `INSTALLED_APPS` in `settings.py`
  3. Apply Django database migrations so that the necessary tables are created: `python manage.py migrate`
  4. Start the celery beat service `celery -A proj beat -l info --scheduler django_celery_beat.schedulers:DatabaseScheduler`
  5. add the related settings if nesscery, [click](http://docs.celeryproject.org/en/latest/userguide/configuration.html#beat-settings-celery-beat) to see more details.
  6. Visit the Django-Admin interface to set up some periodic tasks.

### Daemonization

- In production you’ll want to run the worker in the background as a daemon instead of running the service using commands explicitly.
- If the Server OS uses `systemd` to control all background service. Add the worker files to the .. folder
  - For celery:
  - For Celery Beat:
- run `` to update the deamon settings.
