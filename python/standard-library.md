# Python Standard Library

- All the following libraries are commonly included in Python distributions.
- [Click here](https://docs.python.org/3.8/library/index.html) to view the complete documentation.

## venv

- create new environment `python3 -m venv <envFolderName>`
- activate environment, under project folder `source <envFolderName>/bin/activate`

## itertools modules

### Usage

```py
from itertools import *
count(x) #counts up from x
for i in count(3):
	print(i)
cycle(x) #infinitely iterates through an iterable (for instance a list or string).
repeat(x) #repeats an object, either infinitely or a specific number of times(x).
product(iterable1,iterable2) #return an object contains all possible combination product of these two iterables. (all possible iterable 1 , all possible iterable 2 )
permutation(iterable)   #return an object contains all possible comb for the single iterable.
takewhile(predicateFunc, iterables) # return object with items that only satisfy the predicate function.
chain(x,y) #combine iterables
accumulate(iterables)  #return a object contains a list of sum up to its position.
list(accumulate(range(8)))
```

## re

- It supports Regular Expression.
- `import re`

### Usage

- [Click here](https://huegoxaga.github.io/notes/linux/regex.html) to review Regex Syntax.
- `res = re.findall(r"REpattern", stringName , flags=re.FlagOption)` Pass a string and find all matches base on the Regular Expression pattern, return the result in a list.
  - Flags are optional.
  - The pattern string is not surrounded by `/`. Ex, `r"gr[ae]y"`.
- `result = re.search(substring, string)` search if the `string` contains `substring`, and report the start index and end index if found.
  - `substring` can be replaced by a regular expression pattern.
- Sub-patterns surrounded by `()` in the regex pattern is called groups. e.g. `re.compile(r'(\d\d\d)-(\d\d\d)-(\d\d\d\d)')`
  - The result of the first group can be accessed by using `result.group(1)`
  - The result of the second group can be accessed by using `result.group(2)`
  - The result of all groups can be accessed by using `result.group()`
  - Inside the `()` prepend `?P<groupName>` to give the group a name, then its result can be accessed by using `result.group('groupName')`
- `re.sub(r"pattern", itemToReplace, originalString)` Once a match is found, the second parameter will replace the matched item.
- `re.split(r"pattern", string)` the `string` will be split by the matches into a list, the matches will be deleted and used to separate the `string`.
- `pattern = re.compile(r"pattern")` The pattern will be compiled first and used later.
  - `pattern.search(string)` use the pattern to search.

## urllib

- It is a package that collects several modules for working with URLs:

### urllib.request

- It is used for opening and reading URLs
- `from urllib.request import urlopen`

#### Usage

- `html = urlopen("https://www.example.com/index.html").read()` load the `html` source code of a webpage as string in a variable.
  - `html = urlopen("https://www.example.com/index.html").read().decode('utf-8')` load the webpage that containing special characters from other languages.
  - Indentation and format of the `html` is preserved.

### urllib.parse

- `import urllib.parse`

#### Usage

- `urllib.parse.quote(s)` encode `s` using the `UTF-8` encoding scheme
  - `/` in string `s` will not be encoded
- `urllib.parse.quote(s, safe='')` encode all characted in `s` including `/`
  - `/` is the default `safe` value. Change it to other character will keep that charter intact during encoding.
- `urllib.parse.quote_plus(s)` similar with `.qoute(s)`. It will encoded space as `+`.
- `urllib.parse.urlencode(params)` encode multiple parameters at once using `.qoute_plus(s)`.
  - `params` can be a dictionary like `params = {'key1': 'value1', 'key2': 'value2'}`
- `urllib.parse.urlencode(params, doseq=True)` enable `params` to hold a list as key value.

## urllib3

- `import urllib3`

#### Usage

- `http = urllib3.PoolManager()` create the pool manager to make HTTP calls.
- `r = http.request('GET', url)` make get request
  - `r = http.request('POST', url, fields={'key': 'value'})` post request with parameters.
  - `r = http.request( 'GET', url, headers={})` send get request with a header.
- `r.status` get returning status code
- `r.data` get response as a byte string
- `r.headers` get header info as a dictionary

## webbrowser

- `import webbrowser`

#### Usage

- `webbrowser.open("https://www.google.com/")` open a web page in OS default broswer

## csv

- It works with `.csv` files.
- `import csv`

### Usage

- read a file with default delimter:

  ```py
  with open('filename.csv', 'r') as csv_file:
    csv_reader =csv.reader(csv_file)
  ```

  - `csv_reader` stores a list of list. each list in the list is one row of data that can be accessed by index. Ex, `csv_reader[0][0]` is the first header
    - `csv_reader` can be casted into a list, then used as a list
  - use `csv.reader(csv_file, delimiter='\t')` to set delimiter as `\t`.
  - `next(csv_reader)` will return one line at a time and skip to the next line.
  - use `csv.DictReader(csv_file)` to read csv files into an ordered dictionary. Keys for data in each row are the headers. Use `line['header']` to access data.

  ```py
  with open('filename.csv') as file:
    reader = csv.DictReader(file, delimiter=",")
    for row in reader:
        print(row["headOne"])
        print(int(row["headTwo"]))
  ```

  - `dict_reader.fieldnames` return a list of header names

- write a file with default delimter:

  ```py
  with open('filename.csv', 'r') as csv_file:
    csv_writer =csv.writer(csv_file)
  ```

  - run `csv_writer.writerow("a,b,c")` to write a row to the file.
  - use `csv.writer(csv_file, delimiter='\t')` to set delimiter as `\t`.
  - use `csv.DictWriter(csv_file, fieldnames=listOfHeaders)` to write `csv` files from an ordered dictionary. add `csv_writer.writeheader()` first to write the header to the first line.
  - can use `del line['headerName']` to delete certain field, then to a new file.

## collection

### Counter

- It is used to count the occurrence of data that read by the Counter.
  ```py
  from collection import Counter
  c = Counter()
  c.update(['A','B']) # or c = Counter(['A','B']) in one step
  c.update(['B','C'])
  print(c)
  # output: Counter({'A': 1, 'B': 2, 'C': 1})
  ```
- `c.most_common(10)` return the 10 most common items in the counter. in a list of tuples.

## Queue

- A queue data structure.
- `from queue import Queue`
- `q = Queue()` declare a Queue object.
- `q.put(x)` add element `x` to the queue.
- `q.get()` get the from element from the queue.

## time

- `import time`
- `time.sleep(x)` stop the thread x number of seconds.
- `time.time()` return the system time in seconds.

## threading

- Multi-threading still process one task at one time. It just focus on one thread at first. After some progress is made, it will be focusing on the next thread, instead of complete first one. This is controlled by the global interpreter lock(GIL).
- `import threading as td`

### Usage

- get info
  - `threading.active_count()` count the number of thread
  - `threading.enumerate()` see all threads info
  - `threading.current_thread()` see current thread
- `thread = threading.Thread(target=methodName, name='T1')` define a thread by assigning a method to it.
  - `thread = threading.Thread(target=methodName, name='T1')` define a thread with a name.
  - `t1 = threading.Thread(target=methodName,args=(x,y))` define a thread and pass variables into the method.
- `thread.start()` start the thread.
- `thread.join()` hold all the code following until all previous threads have completed their tasks.
- lock certain block of code in a thread to make sure it is completed before moving on to next thread.
  - `lock = threading.Lock()` declare a lock as global variable.
  - `lock.acquire()` define the beginning of the locked code block.
  - `lock.release()` define the end of the locked code block.
  - `lock` optionally instead of using lock as a global variable, pass `lock` into the methods as a parameter.
  - Data structure `Queue` is usually used to stores a list of result from the multithreading methods.

## multiprocessing

- `import multiprocessing as mp`
- It enables methods to be run on multiple CPU cores.
- All methods of `mp` are identical with `threading`.
- Additionally, Multiprocessing can use `Pool()` and `map()` to auto processing multi-input and return a list of result.
  ```py
  # if processes parameter is omitted, it will use all cores available.
  pool = mp.Pool(processes=2)
  # listX is a list of input for each method.
  res = pool.map(methodName, listX)
  print(res)
  ```
- Use `apply_async()` to start one multiprocessing task.
  ```py
  # only one imput is allowed, the comma followed is required.
  res = pool.apply_async(job, (2,))
  # access result using res.get()
  print(res.get())
  ```
- Interate the `apply_async()` method for multiple tasks.
  ```py
  multi_res =[pool.apply_async(job, (i,)) for i in range(10)]
  print([res.get() for res in multi_res])
  ```
- Multiprocessing methods need to instantiate special object type to access shared variables among cores.
  - `value1 = mp.Value('i', 0)` shared integer values.
  - use `value1.value` to access the the value of the `Value` object.
  - `value2 = mp.Value('d', 3.14)` shared double values.
  - `array = mp.Array('i', [1, 2, 3, 4])` shared array, only 1-D array is supported.
  - `i` or `d` indicate the types for the value, [click to see](https://docs.python.org/3/library/array.html) a complete list of options.

## tkinter

- It is used to create Graphical User Interfaces Apps
- `import tkinter as tk`

### Tkinter Objects

- The GUI is consisted of tkinter objects.
- All GUI objects need to define the location, so it can be added to the Window object. The follow methods are used to define the location.
  - `objectName.pack()` add the object in the center, from top.
    - `objectName.pack(side='bottom')` add the object in the center, from bottom.
    - `objectName.pack(side='right')` add the object in the center, from right.
    - `objectName.pack(side='left')` add the object in the center, from left.
  - `objectName.grid(row=x, column=y, padx=10, pady=10)` using a grid
    - `padx` and `pady` define a grid in the entire window.
    - `row` and `column` define the `x` and `y` location in the grid.
  - `objectName.place(x=20, y=10, anchor='nw')` use an anchor from northwestern corner.
  - These method can also be appended to the object constructor. `tk.Label(window, text="Hello").place(x=20, y=10, anchor='nw')`

##### Window

- `window = tk.Tk()` Window contructor
- `window.title('window title')` set title
- `window.geometry('200x100')` set size
- `window.mainloop()` load window in a loop that listen to any events.

##### Tkinter Variables

- Its content can make the object is assoccoated with rerendered when value is changed.
- `varText = tk.StringVar()` create a string variable.
- `varInt = tk.IntVar()` create a integer variable.
- It can be used as the `textvariable` parameter for other object. `l = tk.Label(window, textvariable=varText)`
- `var.set('new text')` set the text of the string variable.
- It can store list or tuples for listbox's `listvariable` parameter. `var2.set((11,22,33,44))`.

##### Label

- `l = tk.Label(window, text='label text here', bg='blue', font=('Arial', 12), width=15, height=2)` constructor.
  - `window` is the window the label will be in.
  - the unit for width and height is the number of the height and width of a character
- `l.config(text='newText')` change label laproperties including its text if string variable is not used.

##### Button

- `b = tk.Button(window, text='hit me', width=15, height=2, command=functionName)` Constructor.
  - `window` is the window the button will be in.
  - The `command` parameter stores the event handler function.

##### Entry

- This is the input text box.
- `e = tk.Entry(window)` The constructor
  - `e = tk.Entry(window,show='*')` make it a password type input.
- `e.get()` get the user input value.

##### Text

- This is the multi-line input text area.
- `t = tk.Text(window,height=2)` constructor
- `t.insert('insert',varText)` insert some text from string variable into the text field after the cursor position.
- `t.insert('end',varText)` insert some text from string variable into the text field at the end.

##### ListBox

- `lb = tk.Listbox(window, listvariable=var2)`
  - `listvariable` can be a string variable that stores list or tuples.
- `lb.insert('end', "text")` insert `text` at the end
- `lb.insert(0, "text")` insert `text` at the top
- `lb.insert(2, "text")` insert `text` after the second element.
- `lb.delete(2)` delete the third element.
- `lb.get(2)` get the third element value.
- `lb.curselection()` return the index of the selected element.

##### RadioButton

- A single radio button, a group of `Radiobutton` objects is usually used.
- `r1 = tk.Radiobutton(window, text='Option A',variable=var, value='A',command=functionName)` constructor
  - The `variable` parameter will assign the radiobuton `value` to the string variable `var` when the button is selected and then the function will be called.

##### Scale

- It is a horizontal scroll bar for selecting a value.
- `s = tk.Scale(window, label='New Scale', from_=5, to=11, orient=tk.HORIZONTAL, length=200, showvalue=0, tickinterval=2, resolution=0.01, command=functionName)` Scale Constructor.
  - `from_` and `to` set the value range. `from` is a redefined keyword, so `from_` is used.
  - `orient=tk.HORIZONTAL` set the scroll bar oritentation.
  - `length=200` size in pixel.
  - `resolution=0.01` set the value intervals.
  - `showvalue=0` if set to `1`, show selected value on top.
  - `tickinterval=2` set the interval of the labels.
  - An value will be passed into the event handler automatically
    ```py
    def print_selection(x):
      # x is the current selected value of the Scale object
    ```

##### CheckButton

- It is a single check box.
- `c1 = tk.Checkbutton(window, text='option1', variable=intVar, onvalue=1, offvalue=0, command=functionName)` `Checkbutton` constructor
  - `onvalue` this value will be assign to the `variable` parameter when the box is checked.
  - `offvalue` this value will be assign to the `variable` parameter when the box is unchecked.

##### PhotoImage

- It is used to store images.
- `img = tk.PhotoImage(file='filename.png')` Constructor to load image into the variable `img`.

##### Canvas

- A area that can draw shapes on it.
- `shape = tk.Canvas(window, bg='blue', height=100, width=200)` create a canvas
- `shape = canvas.create_line(x0, y0, x1, y1)` create a line.
- `shape = canvas.create_oval(x0, y0, x1, y1, fill='red')` create an oval.
- `shape = canvas.create_arc(x0, y0, x1, y1, start=0, extent=180)` create an arc
- `shape = canvas.create_rectangle(x0, y0, x1, y1)` create a rectangle
- `shape = canvas.create_image(x, y, anchor='nw', image=file)` add an image
  - the `anchor` value `nw` means northwesteron corner. `x` and `y` is the distance from the anchor.
- `canvas.move(shape, x, y)` move the move to the right `x` unit, to the bottom `y` unit.

## os

- Allows access with the Underlying Operating System Functionality

### Usage

- `os.getcwd()` print out the current working directory
- `os.chdir('newPath')` change the working directory
- `os.listdir()` a list of file and folder in the current working directory.
  - `os.listdir('path')`list path in certain directory.
- `os.mkdir()` make one new folder.
- `os.makedirs()` one folder and its sub-folder at once.
- `os.rmdir('path')` remove a foler
- `os.removedirs('path')` remove folders recursively.
- `os.rename('oldNamePath','newNamePath')` rename file.
- `os.stat('filePath')` return file info.
- `os.walk('path')` return three info about all subdirectory for a path.
  ```py
  for root, dirs, files in os.walk('path'):
    print(root, dirs, files)
  ```
- `os.environ` return all environment variables in a dictionary
  - To access `os.environ`, treat it as a dictionary
  - `os.environ.get('ValueName')` get certain environment value.
  - `os.environ['KEY'] = 'Value'` set a environment variable
  - `os.environ.clear()` clear all environment variables
- `os.path.join('folderPath','file')` return a path as `folderPath/file`
- `os.path.basename('path')` return file name of the path.
- `os.path.dirname('path')` return parent directory name of the path.
  - `dirname = os.path.dirname(__file__)` get the dirname of the current file
- `os.path.split('path')` return path name and file name separately.
- `os.path.splitest('path')` return a tuple with file name and its extension with the dot
  - path string should contain at least the filename portion
- `os.path.exist('path')` return true if file exists.
- `os.path.isdir('path')` return true if it is a directory.
- `os.path.isfile('path')` return true if it is a file.
- `os.system('cd ..')` run the command and return the exit status code.

## io

- `import io`
- `file = io.open("temp.jpg", "rb", buffering = 0)` read and stream file from its path as `FileIO` object
  - `file.read()` returns the file's bytes value

### StringIO

- `from io import StringIO`
- `file = StringIO("Hello")` It loads a string as a file object and store it in memory
  - `file.write(" world!")`, `print(file.read())` file can be processed and read as file object without storing the file into the local file system
- `file.getvalue()` returns the entire content of the file

### BytesIO

- It generates memory buffer, It can be used as a file path to the memory. It is fast than storing a file on the disk for further process.
- `from io import BytesIO`
- `buffer = BytesIO(b"Hello \x00\x01")` It saves some bytes value as a file object and store it in memory

## sys

- System-specific parameters and functions
- `import sys`

#### Usage

- `sys.argv` get a list of command line parameters
  - `argv[0]` will always be the script name
- `sys.exit(exit_code)` exit the program with exit code as the argument
  - `0` is the default value, and it indicates a successful termination
  - any value other than `0` indicates an abnormal termination upon exit
  - sometimes, `sys.exit(main(sys.argv))` is used under `if __name__ == '__main__':` block for a good modularized structure
- `sys.stderr.write("Error!\n")` output error messages

## subprocess

- `import subprocess`

### Usage

- `subprocess.run("pbcopy", universal_newlines=True, input="Hello")` add text to the clipboard.

## datetime

### datetime.datetime

- `from datetime import datetime`

#### Usage

- `datetime.fromtimestamp(timestamp)` convert timestamp in second from `1970` to value to datetime object.
- `timestamp = datetime.timestamp(datetime_obj)` convert datetime object to timestamp.
- `datetime_obj = datetime.now()` get a current local datetime object.
  - `time = datetime.now(timezone_obj)` get a current datetime object with a certain timezone.
- `datetime_obj = datetime.utcnow()` get current datetime in UTC
- `datetime.now().time()` get a current time object.
- `datetime_obj.strftime("%m/%d/%Y, %H:%M:%S")` return a formatted time string.
- `date_object = datetime.strptime(date_string, "%d %B, %Y")` string to datetime object
  - [Click Here](https://strftime.org) to see complete list of format code
- `datetime_obj.isoformat()` return datetime in a string in ISO `YYYY-MM-DDThh:mm:ss` format
  - it takes argument like `timespec='microseconds'` for format options
- For datetime object
  - `datetime_obj.year`
  - `datetime_obj.month`
  - `datetime_obj.day`
  - `datetime_obj.hour`
  - `datetime_obj.minute`
  - `datetime_obj.second`
  - `datetime_obj.microsecond`

### datetime.date

- `from datetime import date`

#### Usage

- `date.today()`

### datetime.timedelta

- It can be used to substract or plus a time value to a datetime object
- `timeDeltaObj = timedelta(hours=7, minutes=36)`
- `from datetime import date, timedelta`
- `yesterday = date.today() - timedelta(days=1)`

## time

- `import time`

### Usage

- `time.localtime()` get local time.
- `datetime.combine(date, start_time)` combine a date object and a time object as a datetime object
  - the first second of today, `datetime.combine(date.today(), datetime.min.time()`
  - the last second of today, `datetime.combine(date.today(), datetime.max.time()`

## pytz

- It create a timezone object
- `import pytz`

### Usage

- `myTimeZone = pytz.timezone('Country/City')`
  - `myTimeZone = pytz.timezone('America/New_York')`
- `myTimeZone.localize(datetime)` add timezone info to a datetime object declared without `tz`
- `datetimeObj.replace(tzinfo=myTimeZone)` update a dateime object `tz` info
- `dtWithTZ.astimezone(tz=timezone('America/Toronto')` return the datetime object if it is in another timezone, then update the `tzinfo` for the datetime object.
  - If `dtWithTZ` has no `tzinfo` the `tzinfo` in `astimezone()` will be added and returned
- `dtWithTZ.offset()` return the timedelta for the difference of the dt

## gzip

- It handles data compress and depress

### Usage

- `uncompressed_data = gzip.decompress(compressed_data)` decompress data

## random

- `r = random.randint(start, stop)` return random integer in range `[start, stop]` inclusive
- `r = random.randrange(start, stop, step)` `start` value is optional, default is `0`. `step` value is optional default is `1`

## uuid

- It generates uuid objects.

### uuid objects

- Can use `str()` to cast it to a string.
- x.bytes get the raw 16 bytes of the UUID
- `UUID.hex` The UUID as a 32-character hexadecimal string.
- `UUID.int` The UUID as a 128-bit integer.
- `UUID.urn` The UUID as a URN as specified in RFC 4122.
- `UUID.variant` The UUID variant, which determines the internal layout of the UUID. This will be one of the constants `RESERVED_NCS`, `RFC_4122`, `RESERVED_MICROSOFT`, or `RESERVED_FUTURE`.
- `UUID.version` The UUID version number (1 through 5, meaningful only when the variant is `RFC_4122`).

### Methods

- `uuid.uuid1()` make a UUID based on the host ID and current time
- `uuid.uuid3(uuid.NAMESPACE_DNS, 'python.org')` make a UUID using an MD5 hash of a namespace UUID and a name
- `uuid.uuid4()` make a random UUID
- `uuid.uuid5(uuid.NAMESPACE_DNS, 'python.org')` make a UUID using a SHA-1 hash of a namespace UUID and a name
- `uuid.UUID('{00010203-0405-0607-0809-0a0b0c0d0e0f}')` make a UUID from a string of hex digits (braces and hyphens ignored)

## requests

- It makes HTTP requrests
- `import requests`

### Usage

- `response = requests.get(url, headers=headers)` make get requests when `headers = {'Content-Type': 'application/json', 'Authorization': 'Bearer {0}'.format(token)}`
  - `response.content` get the returning json data as string.
  - `response.text` get the response as a string in unicode
  - `response.status_code` get the response status code.
  - `response.json()` Get the response data as a dictionary.
  - `response.headers` get the header as a dictionary.
  - `response.url` Returns the URL of the response
  - It can pass parameters as `response = requests.get(url, params=parameters, headers=headers)` where `parameters` is a dictionary.

## base64

- Encode/Decode base64 files
- `import base64`

### Usage

- `img = base64.b64decode(img)` decoded base64 images file
- `img = base64.b64encode(bytes)` encode bytes object
  - use `img.decode('utf-8')` to decode it as string in the body of a HTTP response

## json

- It manages python json objects.
- `import json`

### Usage

- `json.loads(jsonObject.decode('utf-8'))` It converts a string into a python object. Typically, it decodes a json object from a string.
- `json.dumps(x)` converts a python object like a list or a dictionary into a string.
- use `with open(FLAGS.json) as f:`, then `data = json.load(f)` to load `.json` file into a dictionary
- use `with open('person.txt', 'w') as json_file:`, then `json.dump(person_dict, json_file)` to write the dictionary to a `.json` file

## csv

- It process `csv` files
- `import csv`

### Usage

- read a `csv` file as arrays, `delimiter` has a default which is `,`,
  ```py
  import csv
  with open('example.csv', 'r',) as file:
      #read csv as arrays
      reader = csv.reader(file, delimiter = '\t')
      for row in reader:
          print(row)
  ```
- read a `csv` file as dictionaries, `delimiter` has a default which is `,`,
  ```py
  import csv
  with open('example.csv', 'r',) as file:
      #read csv as dictionaries
      csv_file = csv.DictReader(file)
      for row in csv_file:
        print(dict(row))
  ```
- write a `csv` file with arrays, `delimiter` has a default which is `,`
  ```py
  import csv
  with open('protagonist.csv', 'w', newline='') as file:
      writer = csv.writer(file, delimiter = '\t')
      # write one row with 1-D array
      writer.writerow(["header_one", "header_two", "header_three"])
      writer.writerow(["first_row_a", "first_row_b", "first_row_c"])
      writer.writerow(["second_row_a", "second_row_b", "second_row_c"])
      # write multiply rows with 2-D array
      writer.writerows([["third_row_a", "third_row_b", "third_row_c"],["fourth_row_a", "fourth_row_b", "fourth_row_c"]])
  ```
- write a `csv` with dictionaries
  ```py
  import csv
  with open('protagonist.csv', 'w', newline='') as file:
      fieldnames = ['header_one', 'header_two', 'header_three']
      writer = csv.DictWriter(file, fieldnames=fieldnames)
      writer.writeheader()
      writer.writerow({'header_one': 'first_row_a', 'header_two': 'first_row_b', 'header_three': 'first_row_c'})
  ```

## unittest

- It is used to do unit testing.
- `import unittest`
- All test method name should start with `test_`
- The order of all test methods is random.

### Assertion Methods

- `assertEqual(a, b)` checks `a == b`
- `assertNotEqual(a, b)` checks `a != b`
- `assertTrue(x)` checks if `bool(x)` is True
- `assertFalse(x)` checks if `bool(x)` is False
- `assertIs(a, b)` checks if `a` is `b`
- `assertIsNot(a, b)` checks if `a` is not `b`
- `assertIsNone(x)` checks if `x` is `None`
- `assertIsNotNone(x)` checks if `x` is not `None`
- `assertIn(a, b)` checks if `a` in `b`
- `assertNotIn(a, b)` checks if `a` not in `b`
- `assertIsInstance(a, b)` checks if `isinstance(a, b)`
- `assertNotIsInstance(a, b)` checks if not `isinstance(a, b)`

### Mock

- create a fake object for testing

#### patch

- `from unittest.mock import patch`
- In the class definition:

  ```py
  def method_for_test(self, t):
        response = requests.get(f'http://company.com/{self.x}/{y}')
        if response.ok:
            return response.text
        else:
            return 'Bad Response!'
  ```

- In the test method:

  ```py
  def test_method(self):
       with patch('classname.requests.get') as mocked_get:
           # create fake response object
           mocked_get.return_value.ok = True
           mocked_get.return_value.text = 'Success'
           schedule = self.object.monthly_schedule('Y')
           # test the called param
           mocked_get.assert_called_with('http://company.com/x/Y/')
           # test mocked response object
           self.assertEqual(schedule, 'Success')
  ```

### Example

```py
class TestExample(unittest.TestCase):
    # Run once at the beginning
    @classmethod
    def setUpClass(cls):
        pass
    # Run once after all test cases.
    @classmethod
    def tearDownClass(cls):
        pass
    # run before every test method
    def setUp(self):
        pass
    # run after every test method
    def tearDown(self):
        pass
    # test method one
    def test_add(self):
        self.assertEqual(calc.add(-1, 1), 0)
        self.assertEqual(calc.add(-1, -1), -2)
    # test method two
    def test_divide(self):
        self.assertEqual(calc.divide(-1, -1), 1)
        self.assertEqual(calc.divide(5, 2), 2.5)
        # Optionally
        with self.assertRaises(ValueError):
            calc.divide(10, 0)
# Enable the test cases run using command 'python filename.py'
# Without the following two lines run 'python -m  unittest filemane.py'
if __name__ == '__main__':
    unittest.main()
```

## logging

- Write output to a log file with different log level
- `import logging`

### Log Level

- `DEBUG` - Detailed information, typically of interest only when diagnosing problems
- `INFO` - Confirmation that things are working as expected.
- `WARNING` - An indication that something unexpected happened, or indicative of some problem in the near future (e.g. ‘disk space low’). The software is still working as expected
- `ERROR` - Due to a more serious problem, the software has not been able to perform some function
- `CRITICAL` - A serious error, indicating that the program itself may be unable to continue running

### Usage

- `logging.basicConfig(filename='example.log', encoding='utf-8', level=logging.DEBUG)`
  - For `python<3.9`, omit the `encoding` argument
- `logging.debug('message')` log debug message
- `logging.info('message')` log info message
- `logging.warning('message')` log warning message
- `logging.error('message')` log error message

## ast

- `myList = ast.literal_eval('["A", "B", "C" , "D"]')` evaluate python literal into tuples, lists, dicts

## hashlib

- It implements a common interface to many different secure hash and message digest algorithms
- `import hashlib`

### Usage

- `m = hashlib.sha256()` constructors for hash algorithm, including:
  - `sha1()`, `sha224()`, `sha256()`, `sha384()`, `sha512()`, `blake2b()`, and `blake2s()` etc
- `m.update(b"Data")` load byte string
- `m.digest()` get hashed result for the loaded data
  - `hashlib.sha256(b"Data").hexdigest()` hash data in one line
- `hash.digest_size` resulting hash size in bytes
- `hash.block_size` The internal block size of the hash algorithm in bytes

## binascii

- It handles conversion between binary data and ASCII characters

### Usage

- `binascii.hexlify(binaryData)` Return the hexadecimal representation of the binary data, every byte of data is converted into the corresponding 2-digit hex representation
- `binascii.a2b_hex(hexstr)` or `binascii.unhexlify(hexstr)` Return the binary data represented by the hexadecimal string hexstr

## contextlib
