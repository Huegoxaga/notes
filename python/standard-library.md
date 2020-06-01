# Python Standard Library

- All the following libraries are commonly included in Python distributions.
- [Click here](https://docs.python.org/3.8/library/index.html) to view the complete documentation.

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
- Sub-patterns surrounded by `()` in the regex pattern is called groups.
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

## csv

- It works with `.csv` files.
- `import csv`

### Usage

- read a file with default delimter:
  ```py
  with open('filename.csv', 'r') as csv_file:
    csv_reader =csv.reader(csv_file)
  ```
  - `csv_reader` stores a list of list. each list in the list is one row of data that can be accessed by index. Ex, `csv_reader[0][0]` is the first header.
  - use `csv.reader(csv_file, delimiter='\t')` to set delimiter as `\t`.
  - `next(csv_reader)` will return one line at a time and skip to the next line.
  - use `csv.DictReader(csv_file)` to read csv files into an ordered dictionary. Keys for data in each row are the headers. Use `line['header']` to access data.
- write a file with default delimter:
  ```py
  with open('filename.csv', 'r') as csv_file:
    csv_writer =csv.writer(csv_file)
  ```
  - run `csv_writer.writerow("a,b,c")` to write a row to the file.
  - use `csv.writer(csv_file, delimiter='\t')` to set delimiter as `\t`.
  - use `csv.DictWriter(csv_file, fieldnames=listOfHeaders)` to write `csv` files from an ordered dictionary. add `csv_writer.writeheader()` first to write the header to the first line.
  - can use `del line['headerName']` to delete certain field, then to a new file.

## collections

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
- `os.environ` return all environment variables in a dictionary.
  - `os.environ.get('ValueName')` get certain environment value.
- `os.path.join('folderPath','file')` return a path as `folderPath/file`
- `os.path.basename('path')` return file name of the path.
- `os.path.dirname('path')` return directory name of the path.
- `os.path.split('path')` return path name and file name separately.
- `os.path.exist('path')` return true if file exists.
- `os.path.isdir('path')` return true if it is a directory.
- `os.path.isfile('path')` return true if it is a file.
- `os.path.splitext('path')` return a file path and an extension of the file separately.

## datetime

### datetime.datetime

- `from datetime import datetime`

#### Usage

- `datetime.fromtimestamp(timestamp)` convert timestamp to value to datetime string.
- `time = datetime.now()` get a current datetime object.
  - `time = datetime.now(timezone_object)` get a current datetime object for a certain timezone.
- `datetime.now().time()` get a current time object.
- `timeObject.strftime("%H:%M:%S")` return a formatted time string.
- For datetime object
  - `time.year`
  - `time.month`
  - `time.day`
  - `time.hour`
  - `time.minute`
  - `time.second`
  - `time.microsecond`

### datetime.date

- `from datetime import date`

#### Usage

- `date.today()`

### datetime.timedelta

- `from datetime import date, timedelta`
- `yesterday = date.today() - timedelta(days=1)`

## time

- `import time`

### Usage

- `time.localtime()` get local time.

## pytz

- It create a timezone object
- `import pytz`

### Usage

- `myTimeZone = pytz.timezone('Country/City')`
  - `myTimeZone = pytz.timezone('America/New_York')`

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
  - `response.status_code` get the response status code.
  - `response.json()` Get the response data as a dictionary.
  - `response.headers` get the header as a dictionary
  - It can pass parameters as `response = requests.get(url, params=parameters, headers=headers)` where `parameters` is a dictionary.

## json

- It manages python json objects.
- `import json`

### Usage

- `json.loads(jsonObject.decode('utf-8'))` It converts a string into a python object. Typically, it decodes a json object from a string.
- `json.dumps(x)` converts a python object like a list or a dictionary into a string.

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

##### patch

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

# def createHash():

# """This function generate 10 character long hash"""

# hash = hashlib.sha1()

# hash.update(str(time.time()))

# return hash.hexdigest()[:-10]

# """This function generate 10 character long hash"""

# return hexlify(os.urandom(5))

import hashlib
import time
import random
from binascii import hexlify
import contextlib
