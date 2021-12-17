# Wiki Scraper

tutorial used: https://www.geeksforgeeks.org/web-scraping-from-wikipedia-using-python-a-complete-guide/

## Intro to Web Scraping and Python

Web scraping is a technique or a process in which large amounts of data from a huge number of websites are passed through a software program to extract the information. Now, we don't have to manually copy and paste the data from websites but the scraper can perform that task in a couple of seconds.

Web scraping is also known as Screen Scraping, Web Data Extraction, and Web Harvesting.

Python is mostly known as the best language for web scraping. Scrapy and Beautiful Soup are among the widely used frameworks based on Python that makes scraping using this language an easy route to take.

## A brief list of Python libraries used for web scraping

1. Requests (HTTP for Humans) Library for Web Scraping - It is used for making various types of HTTP requests like GET, POST, etc. It is the most basic yet the most essential of all libraries.
2. lxml Library for Web Scraping - lxml library provides super-fast and high-performance parsing of HTML and XML content from websites. If you are planning to scrape large datasets, this is the one you should go for.
3. Beautiful Soup Library for Web Scraping - Its work involves creating a parse tree for parsing content. A perfect starting library for beginners and very easy to use.
4. Selenium Library for Web Scraping - Originally made for automated testing of web applications, this library overcomes the issue all the above librares face i.e. scraping content from dynamically populated websites. This makes it slower and not suitable for industry-level projects.
5. Scrapy for Web Scraping - The BOSS of all libraries, an entire web scraping framework which is asynchronous in its usage. This makes it blazing fast and increases efficiency.

## Steps of Web Scraping

![Steps of Web Scraping](/assets/steps_of_web_scraping.png)

### Step 1: How to use python for web scraping?

- We need python IDE to and should be familiar with the use of it.
- Virtualenv is a tool to create isolated Pyhton environments. With the help of virtualenv, we can create a folder tha contains all necessary executables to use the packes that our Python project requires. Here we can add and modify python modules without affecting any global installation.
- WE need to install versious python modules nad libraries using the pip command for our purpose. But, we should always keep in mind that whether the website we are scraping is legal or not.

### Requirements:

- Requests: IT is an efficient library used for accesssing web pages.
- Urlib3: It is used for retrieving data from URLs.
- Selenium: It is an open-source automated testing suite for web applications across different browsers and platforms.

### Installation:

```sh
pip install virtualenv
python -m pip install selenium
python -m pip install requests
python -m pip install urllib3
```

### Step 2: Introduction to Requests library

- Here, we will learn various python modules to fetch data from the web.
- The python requests library is used to make donload the webpage we are trying to scrape.

```python
import requests

page = requests.get('https://en.wikipedia.org/wiki/Main_Page')

print(page.status_code)
print(page.content)
```

### Step 3: Introduction to Beautiful Soup for page parsing

We have a lot of python modules for data extraction. We are going to use BeautifulSoup for our purpose.

- BeautifulSoup is a Python Library for pulling data out of HTML and XML files.
- It needs an input (document or URL) to create a soup object as it cannoy fetch a web apge by itself.
- We have other modules suchs as regular expression, lcml for the same purpose.
- We then process the data in CSV or JSON or MySQL format.

```python
from bs4 import BeautifulSoup
import requests

page = requests.get('https://en.wikipedia.org/wiki/Main_Page')

soup = BeautifulSoup(page.content, 'html.parser')

print(soup.prettify())
```

### Step 4: Digging deep into Beautiful Soup further

Three feaures that make Beautiful Soup so powerful:

- Beautiful Soup provides a few simple methods and Pythonic idioms for navigating, searching, and modifying a parse tree: a toolkit for dissecting a document and extracting what you need. It doesn't take much code to write an application.
- Beautiful Soup automatically converts incoming documents to Unicode and outgoing documents to UTF-8. You don't have to think about encodings unless the document doesn't specify an encoding and Beautiful Soup can't detect one. Then you just have to specify the original encoding.
- Beautiful Soup sits on top of popular Python parsers like lxml and html5lib, allowing you to try out different parsing strategies or trade speed for flexibility. Then we have to just process our data in a proper format such as CSV or JSON or MySQL.

```python
from bs4 import BeautifulSoup
import requests

page = requests.get('https://en.wikipedia.org/wiki/Main_Page')

soup = BeautifulSoup(page.content, 'html.parser')

list (soup.children)

print(soup.find_all('p'))

print ('\n\n')

print(soup.find_all('p')[0].get_text())
```

### Step 5: Exploring page structure with Chrome Dev tools and extracting information

The first thing we'll need to do is inspect the page using Chome Devtools.

You can start the developer tools in Chrome by clicking View -> Developer -> Developer Tools. You should end up at the bottom of the brower like what you see below. The elements will show you all the HTML tags on the page, and let you navigate through them.

![Chrome Devtools](/assets/chrome_tools.png)

```python
from bs4 import BeautifulSoup
import requests

page = requests.get('https://en.wikipedia.org/wiki/Main_Page')

soup = BeautifulSoup(page.content, 'html.parser')

object = soup.find(id='mp-left')

items = object.find_all(class='mp-h2')
result = items[0]

print(result.prettify())
```

![Uses of Web Scraping](/assets/uses_of_web_scraping.png)
