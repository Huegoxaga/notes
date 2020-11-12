# Additional Tools & Packages

## Package Management Tools

### PIP

- `pip` packages are stored on the Python Package Index (PyPI). Here are some useful commands.
- If both python 3 and python 2 is on the system, then running `pip` will update your library for python 2 while `pip3` will update your library for python 3.
- `pip install <packagename>` install a package
  - `pip install <packagename>` is the same as `/usr/bin/python2.7 -m pip install <packagename>`
  - `pip3 install <packagename>` is the same as `/usr/bin/python3.6 -m pip install <packagename>`
- `pip install --upgrade <packagename>` or `pip install -U <packagename>` update a package
  - `--upgrade` can be used for both downgrade or upgrade
- `pip install -r requirements.txt` install packages according the `requirements.txt`
- `pip list --outdated --format=freeze | grep -v '^\-e' | cut -d = -f 1 | xargs -n1 pip install -U` update all packages
- `pip uninstall <packagename>` uninstall a package
- `pip search <keyword>` search for a package
- `pip list` list packages
- `pip freeze` output package info file
  - `pip freeze >requirement.txt` output package info file as txt file.
- `pip list --outdated` list all outdated packages
- Update all packages, in `requirements.txt`, change all `==` to `>=` and run `pip install -r requirements.txt --upgrade`
- `pip show <packagename>` will display the version and location of the installed package

### Conda

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
- `conda config --add channels conda-forge`, add `conda-forge` channel to make it resourceful.
- `conda list` list installed packages and versions installed in active environment
- `conda list --revisions` List the history of each change to the current environment
- `conda info` Verify `conda` is installed, check version number
- `conda search <PackageOrLibrary> --info` check the package or library info and its required dependencies
- `conda update conda` Update conda to the current version
  - `conda update --all` update all packages in the current env
- `conda install <packagename>` Install a package included in Anaconda
  - `conda install <packagename> --file filename.txt` install packages base on text file info.
  - `conda install -c <channelname> <packagename>` install a package from a certain channel
- `conda update <packagename>` Update any installed program
  - `conda update --all` update everything
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
- `conda env export > environment_config_file.yml` generate dependency yaml file
  - Package installed using `pip` will be listed one level lower under `pip:`
- `conda create --name clone_envname --clone envname` Clone an existing environment
- `conda env create -f bio-env.yml` Create environment from a text file
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
  - `array = np.ones_like(img, np.uint8)` create an array of ones with the same shape and type as `img`, with data type as `np.uint8`.(generate a white image with the same size of `img` with unsigned 8 bits integer)
  - optionally, use `np.ones(img.shape, dtype="uint8")`.
- Create an array of zeros
  - `array = np.zeros((2,4))`, a `2*4` array with all elements as 0.
  - Optionally, `dtype` can be its second argument which defines the elements data type.
  - `array = np.zeros_like(img, np.uint8)` create an array of zeros with the same shape and type as `img`, with data type as `np.uint8`.(generate a black image)
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
- Get the max element(s) for array with any demension
  - `np.argmax(array)` the index of the max element of the entire array, the index count from left to right regardless the columns and rows.
  - `np.argmax(array, axis=0)` the indices of the max element along each column.
  - `np.argmax(array, axis=1)` the indices of the max element along each row.

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

- `array.tolist()`, convert to python list and all elements in basic python built-in types
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
- Included in Anaconda
- Dataframe stores data in rows and columns of a table.
- Dataframe is a dictionary structure that has column names as the key. All data for one column is stored in a list from top to bottom as value for the key.
- A column of data is of type series. It has a 1-D list structure.
  - Dataframe is a container for multiple series.
- [Click](https://pandas.pydata.org/docs/reference/index.html) to see the completed documentation for more details.
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
- `dataframe.values` Return a Numpy representation of the DataFrame, axes labels will be removed.
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
  - `df.iloc[0:-1]` returns all rows exclude the last row.
  - `df.iloc[:,-1]` returns the last column.
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

## OpenCV

### Introduction

- OpenCV (Open Source Computer Vision) is a computer vision library that contains various functions to perform operations on pictures or videos.
- It was originally developed by Intel but was later maintained by Willow Garage and is now maintained by Itseez.
- It has C++, C, Python and Java interfaces and supports Windows, Linux, MacOS, iOS and Android.
- It plays a major role in real-time operation for photos and videos.
- Images in openCV are 3-D numpy arrays with `np.uint8` as its elements and three color layer for blue, green and red.
- run `conda install -c menpo opencv` to install
- If using pip, run `pip install opencv-python`

### Usage

- `img = cv2.imread('filePath.jpg', colormode)`, read a image
  - The color mode used to read an image is optional, it can be one of the following options.
    - `cv2.IMREAD_GRAYSCALE` read as a grayscale image
    - `cv2.IMREAD_COLOR` read as a colorful image
    - `h, w = image.shape[:2]` will get the height and width of the image
    - `(B, G, R) = image[x, y]` get the `B`, `R`, `G` color values of one pixel at `(x, y)` on the image.
    - `roi = image[x : h, y : w]` get a rectangle area which starts at the top-left point `(x, y)` with height `h` and width `w`.
- resize
  - `resize = cv2.resize(image, (w, h))` resize an image using area interpolation
  - `scaling_cubic = cv2.resize(image, None, fx=.75, fy=.75, interpolation = cv2.INTER_CUBIC)` Scaling using cubic interpolation
  - `scaling_linear = cv2.resize(image, None, fx=0.5, fy=0.5, interpolation = cv2.INTER_LINEAR)` Scaling using linear interpolation
- flipping
  - `flipping = cv2.flip(image, 1)` Horizontal flipping
  - `flipping = cv2.flip(image, 0)` Vertical Flipping
  - `flipping = cv2.flip(image, -1)` horizontally & vertically flipping
- `gray = cv2.cvtColor(resize_frame, cv2.COLOR_BGR2GRAY)` convert image to grayscale
- Change brightness
  1. `matrix = np.ones(image.shape, dtype = "uint8") * 120` create an array of ones with a brightness factor `120`
  2. `add = cv2.add(image, matrix)` add the brightness to the image.
  3. `subtract = cv2.subtract(image, matrix)` decrease the brightness.
- `output = img1 + img2` image can be added to output an overlaped one since they are numpy arrays.
- `lineType`
  - `cv2.LINE_4` will be medium zigzag pixels in solid color
  - `cv2.LINE_AA` will be wide zigzag pixels in solid and light color
  - `cv2.LINE_8` will one narrow line of pixels in solid color
- Rotation
  - `matrix = cv2.getRotationMatrix2D((x, y), angle, scale)`, Generating a rotation matrix.
    - center – The center coordinates of the image.
    - Angle – The angle (in degrees) by which the image should be rotated
    - Scale – The scaling factor. Ex, `1.0` represents 1 to 1 scale.
  - `rotated = cv2.warpAffine(image, matrix, (w, h))` perform ratation.
    - `matrix` is the rotation matrix that will be performed.
    - `(w, h)` defines the image size after rotation.
  - or, `img = cv2.rotate(img, cv2.ROTATE_180)`
    - `cv2.ROTATE_90_COUNTERCLOCKWISE`
    - `cv2.ROTATE_90_CLOCKWISE`
- blurring
  - blur = cv.GaussianBlur(img,(sizeX,sizeY),0)
    - `0` is the standard deviation in the `X` and `Y` directions
    - `sizeX` is a positive and odd number, represents the width of the kernel
    - `sizeY` is a positive and odd number, represents the height of the kernel
- `output = img.copy()` copy the original image
- `cv2.circle(circle, (100, 100), 100, 255, -1)` circle
- `rectangle = cv2.rectangle(img, (left, top), (bottom, right), (B, G, R), fillMethod)` draw rectangle box on `img`
  - `FillMethod` can be any integer value as line width for bounding box.
  - `-1` will fill the image with bounding box, positive integer numbers indicates the width of the rectanglar bounding box
  - `FillMethod` can be `cv2.FILLED` for a filled rectangle
- `cv2.putText(img, 'Text Content', (x, y), cv2.FONT_HERSHEY_SIMPLEX, 4, (255, 0, 0), 2)` add text on `img`, it uses the following arguments.
  - Image
  - Text to be displayed
  - Bottom-left corner co-ordinates, from where the text should start
  - Font
  - Font size
  - Color (BGR format)
  - Line width
- `image=cv.drawContours(image, contours, contourIdx, color, thickness, lineType, hierarchy, maxLevel, offset)`, draws contours outlines or filled contours. This method will return a smoother shape
  - `image` - Destination image.
  - `contours` - array of contours, 4-D array. Each contour is stored as a point vector.
  - `contourIdx` - Parameter indicating a contour to draw. If it is negative, all the contours are drawn.
  - `color` - Color of the contours.
  - `thickness` - Thickness of lines the contours are drawn with. If it is negative (for example, thickness=FILLED ), the contour interiors are drawn.
  - `lineType` - Line connectivity. See LineTypes
  - `hierarchy` - Optional information about hierarchy. It is only needed if you want to draw only some of the contours (see maxLevel ).
  - `maxLevel` - Maximal level for drawn contours. If it is 0, only the specified contour is drawn. If it is 1, the function draws the contour(s) and all the nested contours. If it is 2, the function draws the contours, all the nested contours, all the nested-to-nested contours, and so on. This parameter is only taken into account when there is hierarchy available.
  - `offset` - Optional contour shift parameter. Shift all the drawn contours by the specified `\(\texttt{offset}=(dx,dy)\)`.
- `img=cv.fillPoly(img, pts, color, lineType)`, Fills the area bounded by one or more polygons.
  - `pts` can be an array of ploygons, each with an array of points. Each point is an array like `[x, y]`. Hence, `pts` holds a 3-D array.
  - `lineType` optional, type of the polygon boundaries.
- bitwise operation
  - `cv.bitwise_not(input, output, mask)` Inverts every bit of an array.
    - `invert = cv2.bitwise_not(white,white, mask=mask)` can be used to find the invert of a mask.
  - `dst=cv.bitwise_and(input1, input2, output, mask)` computes bitwise conjunction of the two arrays. Calculates the per-element bit-wise conjunction of two arrays or an array and a scalar.
    - `mask` optional, 8-bit single channel array, that specifies elements of the output array to be changed.
    - It usually works with mask that output a masked image. Only the white area of a mask will be shown after this operation.
  - `cv.bitwise_not(input)`
  - `cv.bitwise_xor(input, output, mask)`
- `cv2.imshow('image',img)`, showing the stored image
  - The first parameter is the title of title window.
- `imwrite(filename, img)`, save an image to a file
- video
  - `cap = cv2.VideoCapture(0)`, reading video directly from the webcam
    - One camera will be connected by passing `0` OR `-1`
    - Second camera can be selected by passing `2`
  - `cap = cv2.VideoCapture('LOCATION OF THE VIDEO')`, reading a video from local storage
  - `ret, frame = cap.read()`, capture one video frame by frame, if frame is read correctly `ret` is `True`
  - `cap.isOpened()`, check if the video is successfully stored in the variable
    - work well with `while` loop
    - `time.sleep(.05)` in the loop can slow down down the video process speed.
  - `cap.release()`, release the stored video after processing is done
  - `cap.get(3)` check the frame width
  - `cap.get(4)` check the frame height
  - `ret = cap.set(3,320)` or `cap.set(cv.CV_CAP_PROP_FRAME_WIDTH, 320)` modify width
  - `ret = cap.set(4,240)` or `cap.set(cv.CV_CAP_PROP_FRAME_HEIGHT, 240)` modify height
  - Initialize While Loop, read and display frames until `Q` key is pressed.
    ```py
    cap = cv2.VideoCapture(0)
    while(True):
        # Capture frame-by-frame
        ret, frame = cap.read()
        # Our operations on the frame come here
        gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
        # Display the resulting frame
        cv2.imshow('frame',gray)
        if cv2.waitKey(1) & 0xFF == ord('q'):
            break
    # When everything done, release the capture
    cap.release()
    cv2.destroyAllWindows()
    ```
- filter
  - `blur = cv2.blur(image,(9,9))` blur with `9X9` fiter
  - `kernel = np.array([[-1,-1,-1], [-1,9,-1], [-1,-1,-1]])` then `sharpened = cv2.filter2D(image, -1, kernel)` sharpen the image.
- `cv2.waitKey(delay)` The function waitKey waits for a any key event infinitely
  - `delay` – the length of time to wait in milliseconds. `0`(default value) is the special value that means "forever".
  - It returns the key number of the key that has been pressed
- `cv2.destroyAllWindows()` Exit window and destroy all windows
- `cv2.boundingRect(points)` return the bounding rectangle `(x,y,w,h)` of a shape defined as points.
- Classifier
  - `object_detect = cv2.CascadeClassifier('clssifier.xml')` load classifier
  - `cv2.CascadeClassifier.detectMultiScale(img, scaleFactor, minNeighbors)`
    - `scaleFactor`: Specifies the image size to be reduced.
    - `minNeighbors`: Specifies the number of neighbors each rectangle should have to retain it, Higher value results in less detections but with higher quality.
    - It returns `(x,y,w,h)` of the bounding box

## Matplotlib

### Introduction

- It is used to plot graphs.
- [Click](https://matplotlib.org/contents.html#) to see the completed documentation for more details.

### pyplot

- `from matplotlib import pyplot as plt`
- `plt.scatter(X_train, y_train, color = 'red')` plot points
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
- `plt.get_cmap('color_code')` return a list of colors as color map, [Click](https://matplotlib.org/3.1.0/tutorials/colors/colormaps.html) to see all options, color is in RBG and has been divided by `255`

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

## SkiLearn

### sklearn.impute

- SimpleImputer
  - `from sklearn.impute import SimpleImputer`
  - `imputer = SimpleImputer(missing_values=np.nan, strategy='mean')` create an simple imputer object that replace the missing values(numpy nan values) by a certain rule.
    - `'mean'` replace by the average values of all other data.
  - `imputer.fit(X[:, 1:3])` load the imputer object with the target `ndarray` data.
  - `X[:, 1:3] = imputer.transform(X[:, 1:3])` process the data.

### sklearn.compose

- ColumnTransformer
  - `from sklearn.compose import ColumnTransformer`
  - `ct = ColumnTransformer(transformers=[('encoder', OneHotEncoder(), [0])], remainder='passthrough')`
    - transformation type `encoder`
    - encoding type `OneHotEncoder()`
    - columns for encoding `[0]`
    - remiander `passthrough` keep all the remaining column intact
  - `X = np.array(ct.fit_transform(X))` return the encoding result as a `ndarray` object.

### sklearn.preprocessing

- OneHotEncoder
  - `from sklearn.preprocessing import OneHotEncoder`
  - `OneHotEncoder()` it is a type of encoder for multiple categorical values.
- LabelEncoder
  - `from sklearn.preprocessing import LabelEncoder`
  - `le = LabelEncoder()` it is a type of encoder for a binary categorical value(Yes or No).
  - `y = le.fit_transform(y)` return the encoding result.
- StandardScaler
  - `from sklearn.preprocessing import StandardScaler`
  - `sc = StandardScaler()` apply Standardization for feature scaling
  - `X_train[:, 3:] = sc.fit_transform(X_train[:, 3:])` fit will get the mean and standard deviation, transform method will return the standardized value.
  - `X_test[:, 3:] = sc.transform(X_test[:, 3:])` only return the standardized value.
- Image Preprocessing

### sklearn.model_selection

- Splitting test and train data
  - `from sklearn.model_selection import train_test_split`
  - `X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 1)`
    - For return values on the left side.
    - `X` independent variables to split.
    - `y` dependent variables to split.
    - `test_size` `20%` data as test set, `80%` data as training set.
    - `random_state` When equals `1` always return the same spliting result.

### sklearn.linear_model

- Linear Regression Model
  - `from sklearn.linear_model import LinearRegression`
  - `regressor = LinearRegression()` initialize the linear regression model
  - `regressor.fit(X_train, y_train)` training the training data
  - `y_pred = regressor.predict(X_test)` get predict result from test set data points

### sklearn.metrics

- Confusion Matrix
  - `from sklearn.metrics import confusion_matrix`
  - `cm = confusion_matrix(y_test, y_pred)` calculate accurracy

## TensorFlow

- TensorFlow 2.0 uses Keras as its official high-level API
  - Keras is an all in one package for deep learning including both tensorflow and theano
- Install TensorFlow 2.0
  - `tf.__version__` check version
- Import everything
  - `import tensorflow as tf`

### Data Preprocessing

##### Image Preprocessing

- ImageDataGenerator
  - Generate Images based on a certain settings.
    - `train_datagen = ImageDataGenerator(rescale = 1./255, shear_range = 0.2, zoom_range = 0.2, horizontal_flip = True)`
      - `rescale`
      - `shear_range`
      - `zoom_range`
      - `horizontal_flip`
  - Load the images from files.
    - `training_set = train_datagen.flow_from_directory('dataset/training_set', target_size = (64, 64), batch_size = 32, class_mode = 'binary')`
      - First argument is the file path.
      - `target_size`
      - `batch_size`
      - `class_mode`

### Build Model

##### ANN Model

- Define the ANN model as a sequence of layers.
  ```py
  # Initializing the ANN
  ann = tf.keras.models.Sequential()
  # Adding the input layer and the first hidden layer
  ann.add(tf.keras.layers.Dense(output_dim = 6, init = 'uniform', activation='relu', input_dim = 10))
  # Adding the second hidden layer
  ann.add(tf.keras.layers.Dense(output_dim = 6, init = 'uniform', activation='relu'))
  # Adding the output layer using sigmoid for probability
  ann.add(tf.keras.layers.Dense(output_dim = 1, init = 'uniform', activation='sigmoid'))
  ```
  - `output_dim` represents the number of output nodes for the layer.
  - `input_dim` represents the number of input nodes for the layer.
  - `init` represent the ways to initilize weight for the model.

##### CNN Model

- Define the CNN model as a sequence of layers.
  ```py
  # Initializing the CNN
  cnn = tf.keras.models.Sequential()
  # Define the Convolution Layer
  cnn.add(tf.keras.layers.Conv2D(filters=32, kernel_size=3, padding="same", activation="relu", input_shape=[64, 64, 3]))
  # Define the Pooling Layer
  cnn.add(tf.keras.layers.MaxPool2D(pool_size=2, strides=2, padding='valid'))
  # Flattening
  cnn.add(tf.keras.layers.Flatten())
  # Full Connection
  cnn.add(tf.keras.layers.Dense(units=128, activation='relu'))
  # Define the Output Layer
  cnn.add(tf.keras.layers.Dense(units=1, activation='sigmoid'))
  ```
  - `padding` for Layers
    - `same`
    - `valid`

### Compile Model

- Compile the ANNs, `ann.compile(optimizer = 'adam', loss = 'binary_crossentropy', metrics = ['accuracy'])`
- Compile the CNNs, `cnn.compile(optimizer = 'adam', loss = 'binary_crossentropy', metrics = ['accuracy'])`
  - `optimizer` the algorithm for finding the optimized weights.
    - `adam` is a type of stochastic gradient descent algorithm.
  - `loss` define the loss function.
    - `binary_crossentropy` loss function for two outcome.
    - `categorical_crossentropy` loss function for more than two outcome.
  - `metrics` it takes a list of metrics to evaluate the model.
    - `accuracy` based on the accuracy of the model.

### Train Model

- Train ANN model, `ann.fit(X_train, y_train, batch_size = 32, epochs = 100)`
- Train CNN model, `cnn.fit_generator(training_set, steps_per_epoch = 334, epochs = 25, validation_data = test_set, validation_steps = 334)`

### Use Model

- Make prediction, `y_pred = ann.predict(X_test)`
  - separate the results in True or False using a defined metric, `y_pred = (y_pred > 0.5)`

## GDAL

- `conda install -c conda-forge gdal`
- It will install `GDAL` with required`GEOS`, and `Proj`.

## Postgres

- It provide the required driver to connect to a `Postgres` database.
- Run `pip install psycopg2`
- Example Usage

```py
#Import the python driver for PostgreSQL
import psycopg2

#Create a connection credentials to the PostgreSQL database
try:
    connection = psycopg2.connect(
        user = "postgres",
        password = "1234",
        host = "localhost",
        port = "5432",
        database = "demo"
    )

    #Create a cursor connection object to a PostgreSQL instance and print the connection properties.
    cursor = connection.cursor()
    print(connection.get_dsn_parameters(),"\n")

    #Display the PostgreSQL version installed
    cursor.execute("SELECT version();")
    record = cursor.fetchone()
    print("You are connected into the - " record,"\n")

    #Get the column name of a table inside the database and put some values
    pg_insert = """ INSERT INTO book (id, author, isbn, title, date_published)
                VALUES (%s,%s,%s,%s,%s)"""

    inserted_values = (1, 'Layla Nowiztki', '789-1-46-268414-1', 'How to become a professional programmer', 'January 25 2011')

    #Execute the pg_insert SQL string
    cursor.execute(pg_insert, inserted_values)

    #Commit transaction and prints the result successfully
    connection.commit()
    count = cursor.rowcount
    print (count, "Successfully inserted")


#Handle the error throws by the command that is useful when using python while working with PostgreSQL
except(Exception, psycopg2.Error) as error:
    print("Error connecting to PostgreSQL database", error)
    connection = None

#Close the database connection
finally:
    if(connection != None):
        cursor.close()
        connection.close()
        print("PostgreSQL connection is now closed")
```

- `inserted_values` has to be a tuple, even if it has only one parameter. For example, use `(1,)`.

## pyttsx3

- Pyttsx is completely offline and works seemlesly and has multiple tts-engine support.
- By default, the pyttsx3 library loads the best driver available in an operating system: nsss on Mac, sapi5 on Windows and espeak on Linux and any other platform.

### Usage

- pick voice
  ```py
  import pyttsx3
  engine = pyttsx3.init()
  voices = engine.getProperty('voices')
  for voice in voices:
    engine.setProperty('voice', voice.id)
    engine.say('Nice to meet you!')
    engine.runAndWait()
  ```
- female voice pick `voices[10]`, `voices[17]`

## gTTS

- gTTS (Google Text-to-Speech)
- It requires internet connection.
- It writes spoken mp3 data to a file, a file-like object (bytestring) for further audio manipulation, or stdout. Or simply pre-generate Google Translate TTS request URLs to feed to an external program.

## virtualenv

- run `pip` with `sudo` will install the module globally.
- `pip install virtualenv`
- In the project folder run `virtualenv <env_name>` create new env
- `source <env_name>/bin/activate` activate new env
- `deactivate` leave an env

## uwsgi

- The implementation of WSGI, it is used to host Python web app.
- It is written in `C`.
- Installation: `pip install uwsgi`
- Or using conda, run `conda install uwsgi` with `conda-forge` channels.
- `uwsgi --http :8000 --wsgi-file test.py`, Run uWSGI for single page python app
  - `http :8000`: use protocol http, port 8000
  - `wsgi-file test.py`: load the specified page file, `test.py`
- `uwsgi --http :8000 --module wsgi.py`, Run uWSGI for Django app
  - In order to add more functionality to `uWSGI` server. It need to run with another production web server like `Nginx` or `Apache`, configure additional server to link to the `uWSGI`.
    - For this stack, two server will be running at the same time.
- `uwsgi --ini mysite_uwsgi.ini` run uWSGI with `.ini` config file
  - The above parameter can all be in included in the config file

```conf
# mysite_uwsgi.ini file
[uwsgi]

# Django-related settings
# the base directory (full path)
chdir           = /path/to/your/project
# Django's wsgi file
module          = project.wsgi
# the virtualenv (full path)
home            = /path/to/virtualenv

# process-related settings
# master
master          = true
# maximum number of worker processes
processes       = 10
# the socket (use the full path to be safe
socket          = /path/to/your/project/mysite.sock
# ... with appropriate permissions - may be needed
# chmod-socket    = 664
# clear environment on exit
vacuum          = true
```

## Pillow

- Image manipulation package
- `from PIL import Image`

### Usage

- `image = Image.open('image.jpg')` load image
- `exif = imWIthEXIF.info['exif']` get exif data in a dictionary
- `image = Image.fromarray(OpenCVImage)` Convert OpenCV image onto PIL Image
  - `OpenCvImage` is a opencv image object in a numpy array after `cvtColor()`
- `image.save(path, format='JPEG', exif=imWIthEXIF.info['exif'])` save image with exif data as `jpeg`.
- read image with EXIF data using PIL/Pillow, `imgWithEXIF = Image.open(file_path)`, then `exif_data = imgWithEXIF._getexif()`
- convert exif to readable dictionary
  ```py
  from PIL.ExifTags import TAGS
      exif = {
          TAGS[k]: v
          for k, v in exif_data.items()
          if k in TAGS
      }
      print(TAGS)
      print(exif)
  ```
- Generate new metadata
  ```py
  from PIL import Image, TiffTags
  from PIL.TiffImagePlugin import ImageFileDirectory_v2
  import io
  ifd = ImageFileDirectory_v2()
  for k, v in exif_data.items():
      if k in TAGS and k != 34853:
          ifd[k] = v
          # print(TiffTags.lookup(k))
          # print(v)
  out = io.BytesIO()
  ifd.save(out)
  new_exif = b"Exif\x00\x00" + out.getvalue()
  ```

## Abseil

- run `pip install absl-py` to install

### app

- Define the entry point to the python script with flags enabled
- example:

```py
from absl import app
from absl import flags

FLAGS = flags.FLAGS
flags.DEFINE_string("name", None, "Your name.")
flags.DEFINE_integer("num_times", 1,
                     "Number of times to print greeting.")

# Required flag.
flags.mark_flag_as_required("name")

def main(argv):
  del argv  # Unused.
  for i in range(0, FLAGS.num_times):
    print('Hello, %s!' % FLAGS.name)

if __name__ == '__main__':
  app.run(main)
```

### flags

- `from absl import flags`
- `FLAGS = flags.FLAGS` initialize `FLAGS` object
- `flags.DEFINE_string("flag_name", default_value, "description")` define a flag that takes a string
  - `flags.DEFINE_integer('age', None, 'Your age in years.', lower_bound=0)`define a flag that takes a integer
  - `flags.DEFINE_boolean('debug', False, 'Produces debugging output.')`define a flag that takes a boolean
  - `flags.DEFINE_enum('job', 'running', ['running', 'stopped'], 'Job status.')`define a flag that takes a enum
- `FLAGS.flag_name` access flag argument
- `flags.mark_flag_as_required("flag_name")` set a flag as required

### logging

- A logging package implemented on top of the standard `logging` module in Python
- `from absl import logging`
- `logging.info('Interesting Stuff with Arguments: %d', 42)` create a new info level log message
- `logging.set_verbosity(logging.INFO)` only print message with log level higher than `INFO`
- Log level from high to low:
  - `logging.FATAL`
  - `logging.ERROR`
  - `logging.WARNING`
  - `logging.INFO`
  - `logging.DEBUG`
- `logging.log(logging.DEBUG, 'This will *not* be printed')` create a log with `DEBUG` level
- `logging.warning('message')` create warning log
- `logging.error('message')` create error log
- `logging.fatal('message')` create fatal log, and process will exit
