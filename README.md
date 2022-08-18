# beautiful-soup-parsing-tutorial
Using Python &amp; Beautiful Soup to Parse Data


```bash
pip install BeautifulSoup4
```

```html
<!DOCTYPE html>
<html>
    <head>
        <title>What is a Proxy?</title>
        <meta charset="utf-8">
    </head>

    <body>
        <h2>Proxy types</h2>

        <p>
          There are many different ways to categorize proxies. However, two of   
 the most popular types are residential and data center proxies. Here is a list of the most common types.
        </p>

        <ul id="proxytypes">
            <li>Residential proxies</li>
            <li>Datacenter proxies</li>
            <li>Shared proxies</li>
            <li>Semi-dedicated proxies</li>
            <li>Private proxies</li>
        </ul>

    </body>
</html>
```

```python
from bs4 import BeautifulSoup

with open('index.html', 'r') as f:
    contents = f.read()

    soup = BeautifulSoup(contents, features="html.parser")

    for child in soup.descendants:

        if child.name:
            print(child.name)
```

```html
html
head
title
meta
body
h2
p
ul
li
li
li
li
li
```

```python
from bs4 import BeautifulSoup
```

```python
with open('index.html', 'r') as f:
    contents = f.read()
```

```python
    soup = BeautifulSoup(contents, features="html.parser")
```

```python
    for child in soup.descendants:

        if child.name:
            print(child.name)
```

```python
from bs4 import BeautifulSoup

with open('index.html', 'r') as f:
    contents = f.read()

    soup = BeautifulSoup(contents, features="html.parser")

    print(soup.h2)
    print(soup.p)
    print(soup.li)
```

```html
<h2>Proxy types</h2>
<p>
          There are many different ways to categorize proxies.  However, two of the most popular types are residential and data center proxies. Here is a list of the most common types.
        </p>
<li>Residential proxies</li>
```

```python
    print(soup.li.text)
```

```html
Residential proxies
```

```python
    print(soup.find('ul', attrs={'id': 'proxytypes'}))
```

```python
    print(soup.find('ul', id='proxytypes'))
```

```html
<ul id="proxytypes">
<li>Residential proxies</li>
<li>Datacenter proxies</li>
<li>Shared proxies</li>
<li>Semi-dedicated proxies</li>
<li>Private proxies</li>
</ul>
```

```python
   for tag in soup.find_all('li'):
        print(tag.text)
```

```python
from bs4 import BeautifulSoup

with open('index.html', 'r') as f:
    contents = f.read()

    soup = BeautifulSoup(contents, features="html.parser")

    for tag in soup.find_all('li'):
        print(tag.text)
```

```
Residential proxies
Datacenter proxies
Shared proxies
Semi-dedicated proxies
Private proxies
```

```bash
pip install pandas
```

```python
import pandas as pd
```

```python
from bs4 import BeautifulSoup
import pandas as pd

with open('index.html', 'r') as f:
    contents = f.read()

    soup = BeautifulSoup(contents, features="html.parser")
    results = soup.find_all('li')

    df = pd.DataFrame({'Names': results})
    df.to_csv('names.csv', index=False, encoding='utf-8')
```

```python
    results = soup.find_all('li')
```

```python
    df = pd.DataFrame({'Names': results})
    df.to_csv('names.csv', index=False, encoding='utf-8')
```
