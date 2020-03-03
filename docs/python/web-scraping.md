web scraping with python

Regular Expression
import re

# matching string
pattern1 = "cat"
pattern2 = "bird"
string = "dog runs to cat"
print(pattern1 in string)    # True
print(pattern2 in string)    # False
#using in operator


import re

# regular expression
pattern1 = "cat"
pattern2 = "bird"
string = "dog runs to cat"
print(re.search(pattern1, string))
 # <_sre.SRE_Match object; span=(12, 15), match='cat'>
print(re.search(pattern2, string))  
# None

#Using re return details

# multiple patterns ("run" or "ran")
ptn = r"r[au]n"       # start with "r" means raw string
print(re.search(ptn, "dog runs to cat"))    # <_sre.SRE_Match object; span=(4, 7), match=‘run'>

#Using expression with format r”content[multiple possibility]”


print(re.search(r"r[A-Z]n", "dog runs to cat"))     # None
print(re.search(r"r[a-z]n", "dog runs to cat"))     # <_sre.SRE_Match object; span=(4, 7), match='run'>
print(re.search(r"r[0-9]n", "dog r2ns to cat"))     # <_sre.SRE_Match object; span=(4, 7), match='r2n'>
print(re.search(r"r[0-9a-z]n", "dog runs to cat"))  # <_sre.SRE_Match object; span=(4, 7), match=‘run'>


#More situation.





# \d : decimal digit
print(re.search(r"r\dn", "run r4n"))           # <_sre.SRE_Match object; span=(4, 7), match='r4n'>
# \D : any non-decimal digit
print(re.search(r"r\Dn", "run r4n"))           # <_sre.SRE_Match object; span=(0, 3), match='run'>
# \s : any white space [\t\n\r\f\v]
print(re.search(r"r\sn", "r\nn r4n"))          # <_sre.SRE_Match object; span=(0, 3), match='r\nn'>
# \S : opposite to \s, any non-white space
print(re.search(r"r\Sn", "r\nn r4n"))          # <_sre.SRE_Match object; span=(4, 7), match='r4n'>
# \w : [a-zA-Z0-9_]
print(re.search(r"r\wn", "r\nn r4n"))          # <_sre.SRE_Match object; span=(4, 7), match='r4n'>
# \W : opposite to \w
print(re.search(r"r\Wn", "r\nn r4n"))          # <_sre.SRE_Match object; span=(0, 3), match='r\nn'>
# \b : empty string (only at the start or end of the word)
print(re.search(r"\bruns\b", "dog runs to cat"))    # <_sre.SRE_Match object; span=(4, 8), match='runs'>
# \B : empty string (but not at the start or end of a word)
print(re.search(r"\B runs \B", "dog   runs  to cat"))  # <_sre.SRE_Match object; span=(8, 14), match=' runs '>
# \\ : match \
print(re.search(r"runs\\", "runs\ to me"))     # <_sre.SRE_Match object; span=(0, 5), match='runs\\'>
# . : match anything (except \n)
print(re.search(r"r.n", "r[ns to me"))         # <_sre.SRE_Match object; span=(0, 3), match='r[n'>
# ^ : match line beginning
print(re.search(r"^dog", "dog runs to cat"))   # <_sre.SRE_Match object; span=(0, 3), match='dog'>
# $ : match line ending
print(re.search(r"cat$", "dog runs to cat"))   # <_sre.SRE_Match object; span=(12, 15), match='cat'>
# ? : may or may not occur
print(re.search(r"Mon(day)?", "Monday"))       # <_sre.SRE_Match object; span=(0, 6), match='Monday'>
print(re.search(r"Mon(day)?", "Mon"))          # <_sre.SRE_Match object; span=(0, 3), match=‘Mon'>


\letter  means all context within this category.


string = """
dog runs to cat.
I run to dog.
"""
print(re.search(r"^I", string))                 # None
print(re.search(r"^I", string, flags=re.M))     # <_sre.SRE_Match object; span=(18, 19), match='I'>


# * : occur 0 or more times
print(re.search(r"ab*", "a"))             # <_sre.SRE_Match object; span=(0, 1), match='a'>
print(re.search(r"ab*", "abbbbb"))        # <_sre.SRE_Match object; span=(0, 6), match='abbbbb'>

# + : occur 1 or more times
print(re.search(r"ab+", "a"))             # None
print(re.search(r"ab+", "abbbbb"))        # <_sre.SRE_Match object; span=(0, 6), match='abbbbb'>

# {n, m} : occur n to m times
print(re.search(r"ab{2,10}", "a"))        # None
print(re.search(r"ab{2,10}", "abbbbb"))   # <_sre.SRE_Match object; span=(0, 6), match=‘abbbbb'>

match = re.search(r"(\d+), Date: (.+)", "ID: 021523, Date: Feb/12/2017")
print(match.group())                   
# 021523, Date: Feb/12/2017
print(match.group(1))                 
 # 021523
print(match.group(2))                  
# Date: Feb/12/2017

#find different condition in groups and retrieved by group number.

match = re.search(r"(?P<id>\d+), Date: (?P<date>.+)", "ID: 021523, Date: Feb/12/2017")
print(match.group('id'))                # 021523
print(match.group('date'))              # Date: Feb/12/2017

#find different condition in groups and retrieved by group name.


# findall
print(re.findall(r"r[ua]n", "run ran ren"))    # ['run', 'ran']

# | : or
print(re.findall(r"(run|ran)", "run ran ren")) # ['run', ‘ran’]
#return all result in a list.

print(re.sub(r"r[au]ns", "catches", "dog runs to cat"))     # dog catches to cat
#display a replaced result.

print(re.split(r"[,;\.]", "a;b,c.d;e"))             # ['a', 'b', 'c', 'd', ‘e']
#return a result splited by the rules in [] and \ is an  escape character.


compiled_re = re.compile(r"r[ua]n")
print(compiled_re.search("dog ran to cat"))  # <_sre.SRE_Match object; span=(4, 7), match=‘ran'>

#save the rules first and then use rules to search.






This is a example using urlopen for web scraping

from urllib.request import urlopen    

# if has Chinese, apply decode()
html = urlopen("https://morvanzhou.github.io/static/scraping/basic-structure.html").read().decode('utf-8')
print(html)

import re
res = re.findall(r"<title>(.+?)</title>", html)
print("\nPage title is: ", res[0])  

#This code is used to read content in the <title> tag.

res = re.findall(r"<p>(.*?)</p>", html, flags=re.DOTALL)    # re.DOTALL if multi line
print("\nPage paragraph is: ", res[0])

#This code is used to read content in the <p> tag.

res = re.findall(r'href="(.*?)"', html)
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
    print(m.get_text())  #get_text is method for pure content without tags.
#This uses class tag from css code.


jan = soup.find('ul', {"class": 'jan'})
d_jan = jan.find_all('li')              # use jan as a parent
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

img_links = soup.find_all("img", {"src": re.compile('.*?\.jpg')})
for link in img_links:
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
print(soup.find('h1').get_text(), '    url: ', his[-1])
#find return the first result

# find valid urls
sub_urls = soup.find_all("a", {"target": "_blank", "href": re.compile("/item/(%.{2})+$")})

if len(sub_urls) != 0:
    his.append(random.sample(sub_urls, 1)[0]['href'])
else:
    # no valid sub link found
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
param = {"wd": “莫烦Python"}
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
urlretrieve(IMAGE_URL, './img/image1.png')      # whole document










#Using request
import requests
r = requests.get(IMAGE_URL)
with open('./img/image2.png', 'wb') as f:
    f.write(r.content)

r = requests.get(IMAGE_URL, stream=True)    # stream loading

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
    time.sleep(0.1)      #pretend to wait slightly delay for downloading
    return response.read().decode()


def parse(html):
    soup = BeautifulSoup(html, 'lxml')
    urls = soup.find_all('a', {"href": re.compile('^/.+?/$')})
    title = soup.find('h1').get_text().strip()
    page_urls = set([urljoin(base_url, url['href']) for url in urls])
    url = soup.find('meta', {'property': "og:url"})['content']
    return title, page_urls, url


Normal way:
unseen = set([base_url,])
seen = set()

count, t1 = 1, time.time()

while len(unseen) != 0:                 # still get some url to visit
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
print('Total time: %.1f s' % (time.time()-t1, ))    # 53 s

Multiprocessing:
unseen = set([base_url,])
seen = set()

pool = mp.Pool(4)                       
count, t1 = 1, time.time()
while len(unseen) != 0:                 # still get some url to visit
    if restricted_crawl and len(seen) > 20:
            break
    print('\nDistributed Crawling...')
    crawl_jobs = [pool.apply_async(crawl, args=(url,)) for url in unseen]
    htmls = [j.get() for j in crawl_jobs]                                       # request connection

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
print('Total time: %.1f s' % (time.time()-t1, ))    # 16 s !!!

Asyncio tutorial

import time
#normal way

def job(t):
    print('Start job ', t)
    time.sleep(t)               # wait for "t" seconds
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
    await asyncio.sleep(t)          # wait for "t" seconds, it will look for another job while await
    print('Job ', t, ' takes ', t, ' s')


async def main(loop):
    tasks = [loop.create_task(job(t)) for t in range(1, 3)]     # just create, not run job
    await asyncio.wait(tasks)                                   # run jobs and wait for all tasks done

t1 = time.time()
loop = asyncio.get_event_loop()
loop.run_until_complete(main(loop))
# loop.close()                          # Ipython notebook gives error if close loop
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
        all_results = [r.result() for r in finished]        # get return from job
        print(all_results)

t1 = time.time()
loop = asyncio.get_event_loop()
loop.run_until_complete(main(loop))
# loop.close()                      # Ipython notebook gives error if close loop
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
    ]
    # unseen = set()
    # seen = set()      # we don't need these two as scrapy will deal with them automatically

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
