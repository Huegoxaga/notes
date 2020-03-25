# Python Standard Library

- All the following libraries are commonly included in Python distributions.
- [Click here](https://docs.python.org/3.8/library/index.html) to view the complete documentation.

## `re`

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

## `urllib`

- It is a package that collects several modules for working with URLs:

### `urllib.request`

- It is used for opening and reading URLs
- `from urllib.request import urlopen`

#### Usage

- `html = urlopen("https://www.example.com/index.html").read()` load the `html` source code of a webpage as string in a variable.
  - `html = urlopen("https://www.example.com/index.html").read().decode('utf-8')` load the webpage that containing special characters from other languages.
  - Indentation and format of the `html` is preserved.

## `csv`

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

## `collections`

### `Counter`

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

## `Queue`

- A queue data structure.
- `from queue import Queue`
- `q = Queue()` declare a Queue object.
- `q.put(x)` add element `x` to the queue.
- `q.get()` get the from element from the queue.

## `time`

- `import time`
- `time.sleep(x)` stop the thread x number of seconds.
- `time.time()` return the system time in seconds.

## `threading`

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

## `multiprocessing`

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

## `tkinter`

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

This is a example using urlopen for web scraping

from urllib.request import urlopen

# if has Chinese, apply decode()

html = urlopen("https://morvanzhou.github.io/static/scraping/basic-structure.html").read().decode('utf-8')
print(html)

import re
res = re.findall(r"<title>(.+?)</title>", html)
print("\nPage title is: ", res[0])

#This code is used to read content in the <title> tag.

res = re.findall(r"<p>(.\*?)</p>", html, flags=re.DOTALL) # re.DOTALL if multi line
print("\nPage paragraph is: ", res[0])

#This code is used to read content in the <p> tag.

res = re.findall(r'href="(.\*?)"', html)
print("\nAll links: ", res

#This code is used to read content in the <a> tag.

beautiful soup

install
for python3 in console type
pip3 install beautiful4

from bs4 import BeautifulSoup
from urllib.request import urlopen

# if has Chinese, apply decode()

html = urlopen("https://morvanzhou.github.io/static/scraping/basic-structure.html").read().decode('utf-8')
print(html)

#load content to soup
soup = BeautifulSoup(html, features='lxml')
print(soup.h1)
print('\n', soup.p)

#This code is used to read content in the <h1> or <p> tag.

all_href = soup.find_all('a')
all_href = [l['href'] for l in all_href]
print('\n', all_href)

#This finds all links

month = soup.find_all('li', {"class": "month"})
for m in month:
print(m.get_text()) #get_text is method for pure content without tags.
#This uses class tag from css code.

jan = soup.find('ul', {"class": 'jan'})
d_jan = jan.find_all('li') # use jan as a parent
for d in d_jan:
print(d.get_text())

This is used to find content in a tag of a class.

Combine RE and soup

from bs4 import BeautifulSoup
from urllib.request import urlopen
import re

# if has Chinese, apply decode()

html = urlopen("https://morvanzhou.github.io/static/scraping/table.html").read().decode('utf-8')
print(html)
soup = BeautifulSoup(html, features='lxml')

img*links = soup.find_all("img", {"src": re.compile('.*?\.jpg')})
for link in img*links:
print(link[‘src'])
course_links = soup.find_all('a', {'href': re.compile('https://morvan.*')})
for link in course_links:
print(link[‘href’])

Example code:

from bs4 import BeautifulSoup
from urllib.request import urlopen
import re
import random

base_url = "https://baike.baidu.com"
his = [“/item/%E7%BD%91%E7%BB%9C%E7%88%AC%E8%99%AB/5162711"]

url = base_url + his[-1]

html = urlopen(url).read().decode('utf-8')
soup = BeautifulSoup(html, features='lxml')
print(soup.find('h1').get_text(), ' url: ', his[-1])
#find return the first result

# find valid urls

sub_urls = soup.find_all("a", {"target": "\_blank", "href": re.compile("/item/(%.{2})+\$")})

if len(sub_urls) != 0:
his.append(random.sample(sub_urls, 1)[0]['href'])
else: # no valid sub link found
his.pop()
print(his)

#find all url

his = ["/item/%E7%BD%91%E7%BB%9C%E7%88%AC%E8%99%AB/5162711"]

for i in range(20):
url = base_url + his[-1]

    html = urlopen(url).read().decode('utf-8')
    soup = BeautifulSoup(html, features='lxml')
    print(i, soup.find('h1').get_text(), '    url: ', his[-1])

    # find valid urls
    sub_urls = soup.find_all("a", {"target": "_blank", "href": re.compile("/item/(%.{2})+$")})

    if len(sub_urls) != 0:
        his.append(random.sample(sub_urls, 1)[0]['href'])
    else:
        # no valid sub link found
        his.pop()

For post and get access

Using requests to get online data

pip install requests
pip3 install requests

import requests
import webbrowser
#for get request
#get result into r directly
param = {"wd": “莫烦 Python"}
#this generate auto url for the wd keyword.
r = requests.get('http://www.baidu.com/s', params=param)
print(r.url)
#open browser within the program
webbrowser.open(r.url)

#for post request
#post data into server, and save result into r
data = {'firstname': '莫烦', 'lastname': '周'}
r = requests.post('http://pythonscraping.com/files/processing.php', data=data)
print(r.text)

upload image
file = {'uploadFile': open('./image.png', 'rb')}
r = requests.post('http://pythonscraping.com/files/processing2.php', files=file)
print(r.text)

login

payload = {'username': 'Morvan', 'password': 'password'}
r = requests.post('http://pythonscraping.com/pages/cookies/welcome.php', data=payload)
print(r.cookies.get_dict())
#cookies is mandatory to keep the connection.
r = requests.get('http://pythonscraping.com/pages/cookies/profile.php', cookies=r.cookies)
print(r.text)

another login method

#using session control cookie.
session = requests.Session()
payload = {'username': 'Morvan', 'password': 'password'}
r = session.post('http://pythonscraping.com/pages/cookies/welcome.php', data=payload)
print(r.cookies.get_dict())
r = session.get("http://pythonscraping.com/pages/cookies/profile.php")
print(r.text)

download files

import os
os.makedirs('./img/', exist_ok=True)

IMAGE_URL = “https://morvanzhou.github.io/static/img/description/learning_step_flowchart.png"

#using urltrtrieve
from urllib.request import urlretrieve
urlretrieve(IMAGE_URL, './img/image1.png') # whole document

#Using request
import requests
r = requests.get(IMAGE_URL)
with open('./img/image2.png', 'wb') as f:
f.write(r.content)

r = requests.get(IMAGE_URL, stream=True) # stream loading

with open('./img/image3.png', 'wb') as f:
for chunk in r.iter_content(chunk_size=32):
f.write(chunk)

from bs4 import BeautifulSoup
import requests

URL = “http://www.nationalgeographic.com.cn/animals/"

html = requests.get(URL).text
soup = BeautifulSoup(html, 'lxml')
img_ul = soup.find_all('ul', {"class": “img_list"})

import os

os.makedirs('./img/', exist_ok=True)

for ul in img_ul:
imgs = ul.find_all('img')
for img in imgs:
url = img['src']
r = requests.get(url, stream=True)
image_name = url.split('/')[-1]
with open('./img/%s' % image_name, 'wb') as f:
for chunk in r.iter_content(chunk_size=128):
f.write(chunk)
print('Saved %s' % image_name)

import multiprocessing as mp
import time
from urllib.request import urlopen, urljoin
from bs4 import BeautifulSoup
import re

base_url = "http://127.0.0.1:4000/"

# base_url = 'https://morvanzhou.github.io/'

# DON'T OVER CRAWL THE WEBSITE OR YOU MAY NEVER VISIT AGAIN

if base_url != "http://127.0.0.1:4000/":
restricted_crawl = True
else:
restricted_crawl = False

def crawl(url):
response = urlopen(url)
time.sleep(0.1) #pretend to wait slightly delay for downloading
return response.read().decode()

def parse(html):
soup = BeautifulSoup(html, 'lxml')
urls = soup.find_all('a', {"href": re.compile('^/.+?/\$')})
title = soup.find('h1').get_text().strip()
page_urls = set([urljoin(base_url, url['href']) for url in urls])
url = soup.find('meta', {'property': "og:url"})['content']
return title, page_urls, url

Normal way:
unseen = set([base_url,])
seen = set()

count, t1 = 1, time.time()

while len(unseen) != 0: # still get some url to visit
if restricted_crawl and len(seen) > 20:
break

    print('\nDistributed Crawling...')
    htmls = [crawl(url) for url in unseen]

    print('\nDistributed Parsing...')
    results = [parse(html) for html in htmls]

    print('\nAnalysing...')
    seen.update(unseen)         # seen the crawled
    unseen.clear()              # nothing unseen

    for title, page_urls, url in results:
        print(count, title, url)
        count += 1
        unseen.update(page_urls - seen)     # get new url to crawl

print('Total time: %.1f s' % (time.time()-t1, )) # 53 s

Multiprocessing:
unseen = set([base_url,])
seen = set()

pool = mp.Pool(4)  
count, t1 = 1, time.time()
while len(unseen) != 0: # still get some url to visit
if restricted_crawl and len(seen) > 20:
break
print('\nDistributed Crawling...')
crawl_jobs = [pool.apply_async(crawl, args=(url,)) for url in unseen]
htmls = [j.get() for j in crawl_jobs] # request connection

    print('\nDistributed Parsing...')
    parse_jobs = [pool.apply_async(parse, args=(html,)) for html in htmls]
    results = [j.get() for j in parse_jobs]                                     # parse html

    print('\nAnalysing...')
    seen.update(unseen)         # seen the crawled
    unseen.clear()              # nothing unseen

    for title, page_urls, url in results:
        print(count, title, url)
        count += 1
        unseen.update(page_urls - seen)     # get new url to crawl

print('Total time: %.1f s' % (time.time()-t1, )) # 16 s !!!

Asyncio tutorial

import time
#normal way

def job(t):
print('Start job ', t)
time.sleep(t) # wait for "t" seconds
print('Job ', t, ' takes ', t, ' s')

def main():
[job(t) for t in range(1, 3)]

t1 = time.time()
main()
print("NO async total time : ", time.time() - t1)

#using asyncio
import asyncio

async def job(t):
print('Start job ', t)
await asyncio.sleep(t) # wait for "t" seconds, it will look for another job while await
print('Job ', t, ' takes ', t, ' s')

async def main(loop):
tasks = [loop.create_task(job(t)) for t in range(1, 3)] # just create, not run job
await asyncio.wait(tasks) # run jobs and wait for all tasks done

t1 = time.time()
loop = asyncio.get_event_loop()
loop.run_until_complete(main(loop))

# loop.close() # Ipython notebook gives error if close loop

print("Async total time : ", time.time() - t1)

#normal way for scraping
import requests

URL = 'https://morvanzhou.github.io/'

def normal():  
 for i in range(2):
r = requests.get(URL)
url = r.url
print(url)

t1 = time.time()
normal()
print("Normal total time:", time.time()-t1)

#using aiohttp from saync
import aiohttp

async def job(session):
response = await session.get(URL)
return str(response.url)

async def main(loop):
async with aiohttp.ClientSession() as session:
tasks = [loop.create_task(job(session)) for _ in range(2)]
finished, unfinished = await asyncio.wait(tasks)
all_results = [r.result() for r in finished] # get return from job
print(all_results)

t1 = time.time()
loop = asyncio.get_event_loop()
loop.run_until_complete(main(loop))

# loop.close() # Ipython notebook gives error if close loop

print("Async total time:", time.time() - t1)
Selenium generate user behaviour into code and run in python code
1 pip install selenium
2 driver for brewer copy heckodriver to bin(chmod +m)

For firefox katalonrecorder is easier to add as addons.

Scrapy library
advanced automatically tools for scraping

pip install scrapy
import scrapy

class MofanSpider(scrapy.Spider):
name = "mofan"
start_urls = [
'https://morvanzhou.github.io/',
] # unseen = set() # seen = set() # we don't need these two as scrapy will deal with them automatically

    def parse(self, response):
        yield {     # return some results
            'title': response.css('h1::text').extract_first(default='Missing').strip().replace('"', ""),
            'url': response.url,
        }

        urls = response.css('a::attr(href)').re(r'^/.+?/$')     # find all sub urls
        for url in urls:
            yield response.follow(url, callback=self.parse)     # it will filter duplication automatically

# lastly, run this in terminal

# scrapy runspider 5-2-scrapy.py -o res.json
