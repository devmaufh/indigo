---
title: "Reading data from URL using Python"
layout: post
date: 2019-01-08 10:50
image: https://cdn-images-1.medium.com/max/1600/1*7EUX9QIjq2x1JyFKcjhXsA.png
headerImage: true
tag:
- Python
- Data
category: blog
author: johndoe
description: This is simple example for how to read a data set from a url using python and Pandas
# jemoji: '<img class="emoji" title=":ramen:" alt=":ramen:" src="https://assets.github.com/images/icons/emoji/unicode/1f35c.png" height="20" width="20" align="absmiddle">'
---
# What is a data set?

According [Wikipedia](https://en.wikipedia.org/wiki/Data_set) 

>data set is a collection of data. Most commonly a data set corresponds to the contents of a single database table, or a single statistical data matrix, where every column of the table represents a particular variable, and each row corresponds to a given member of the data set in question.

We can find a data set in many kind of files like **CSV**,**XML**,**HTML**,**XLS** just for say a few. In this post we're going to use a **CSV**.

---
# What do you need?
- Python
- Pandas library
- Text editor
- Coffe :coffee:

---
## Let's do it
First of all open your text editor and create a new python file. I always recommend [Atom](https://atom.io) or [Visual studio code](https://code.visualstudio.com/) both are free.

We need to import [Pandas](https://pandas.pydata.org/) which is a powerfull library written for data manipulation and analysis.

```python
import pandas as pd
```

Then we define the url of our data set, in this case i'm using a data set of winter olympics medals, you can use whatever you want. 
```python
dataset_url="http://winterolympicsmedals.com/medals.csv"
```

Now we have to read our data set with pandas, this is very easy beacause **Pandas** does all the hard work. So we onlye have to type this lines of code:
```python
dataset=pd.read_csv(dataset_url)
```
¡And that's it! If you want to verify that all works fine, add this line to get data head of our data set:
```python
print(dataset.head())
```

<img src="{{ site.url }}/assets/images/readingdatasethead.png" alt="data-head" title="A cute kitten"/>

Or this to get data tail:
```python
print(dataset.tail())
```

Your completly code should look like this:
```python
import pandas as pd
dataset_url="http://winterolympicsmedals.com/medals.csv"
dataset=pd.read_csv(dataset_url)
print(dataset.head())
```

---
You can find this code on my [Github](https://github.com/devmaufh/data-science/blob/master/readingFromUrlPandas.py)