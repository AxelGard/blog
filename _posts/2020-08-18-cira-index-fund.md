---
layout: post
title:  "Build a index fund with Cira"
date:   2020-08-20 20:00:00 +0200
categories: cira
---

## basics 
The fund will be buying and selling at random stocks from nasdaq giving a portfolio that follows the market. 

### Installation
You can install by [pip](https://pypi.org/project/cira/)
```bash
pip install cira
```

Becose the [alpca trade API](https://alpaca.markets/) need a key. <br> 
You need to keep your api key in a **json file**. Cira needs the **path** to the file.

**key.json**
```json 
{
  "APCA-API-KEY-ID":"your_pub_key",
  "APCA-API-SECRET-KEY":"your_private_key"
}
```
Then you can start using the lib.
```python 
import cira
cira.KEY_FILE = "../mypath/key.json"
```

### Getting started

First you will need to a main loop. 
This will call a function caled **instance()**
```python
import cira
import time 

cira.KEY_FILE = "../mypath/key.json"

while True: 
  if cira.exchange_open():
  instance()
  time.sleep(60*30) # 30 min timer 
```

### The instance 
the function instance is not a must but is a way to keep track of the behavior of the bot.
So let's keep it simpel.

```python
def instance():
  """ This func is the main behavior """
  random_buy()
  random_sell()

```

## helper functions  
These are the functions that help the instance to preform the actions.
A way of thinking of a function is that it shuld do one thing.


```python
import cira
import time
import random

cira.KEY_FILE = "../mypath/key.json"

def random_stock():
  """ returns a random stock from NASDAQ  """
  market_assets = cira.nasdaq_assets()
  return market_assets[random.randint(0, len(market_assets))].symbol


def random_buy():
  """ buy a random stock """
  qty = random.randint(1, 100)
  sym = random_stock()
  return cira.buy(qty, sym)


def random_sell():
    """ sells random stock """
    qty = random.randint(1, 100)
    ownd_stocks = cira.owned_stocks()
    sym = ownd_stocks[random.randint(0, len(ownd_stocks)-1)]
    return cira.sell(qty, sym)


def instance():
  """ This func is the main behavior """
  random_buy()
  random_sell()


while True: 
  if cira.exchange_open():
    instance()
    time.sleep(60*30) # 30 min timer

```

We are now done!
konw you can runit and test it 

```bash
python3 myfund.py
```