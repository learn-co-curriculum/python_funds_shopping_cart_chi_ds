
## Python Fundamentals Part II

**Scenario:** Today we are going to build our knowledge about for loops and functions. Who has ever got to the cash register at costco, or whole foods, seen the total and asked "how did I spend that much?". Today we have a grocery list of items and prices, but we do not have infinite money (unfortunately), so we need to have a program that will look at our grocery list and help us manage our shopping and cost.

### Learning goals:

In this notebook we will:
 - practice for loops
 - use `break` to adjust loop activity
 - use nested loops to navigate a nested dictionary
 - write a robust function that will take any nested dictionary of items, costs, and print out your shopping list, stopping when the total cost gets to high, and telling you the average cost per item in your cart.


Let's revisit what a for loop does. Here we have a list of items, and a separate list of costs. We are going to write a loop to print each item, it's cost, and the total of our grocery list.

```
items = ['cheese', 'whole milk', 'kefir', 'tofu four-pack', 'kale', 'oranges', 'ham', 'ben & jerry's']
cost = [2.79, 3.42, 4.50, 12.00, 2.75, 3.64, 25.00, 5.29]
```

![groc-cart](https://images.pexels.com/photos/1389103/pexels-photo-1389103.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260)

### For loops:
First, let's create a for-loop that prints each item in the list with "I need to buy: " item.


```python
items = ['cheese', 'whole milk', 'kefir', 'tofu four-pack', 
         'kale', 'oranges', 'ham', 'ben & jerry\'s']
cost = [2.79, 3.42, 4.50, 12.00, 2.75, 3.64, 25.00, 5.29]

for food in items:
    print(food)
        
```

    cheese
    whole milk
    kefir
    tofu four-pack
    kale
    oranges
    ham
    ben & jerry's


Let's make that a little nicer looking:



```python
print("I need to buy: ")
for item in items:
   print(" - [ ] ", item)
```

    I need to buy: 
     - [ ]  cheese
     - [ ]  whole milk
     - [ ]  kefir
     - [ ]  tofu four-pack
     - [ ]  kale
     - [ ]  oranges
     - [ ]  ham
     - [ ]  ben & jerry's


We learned earlier how to use [zip](https://www.w3schools.com/python/ref_func_zip.asp).  Let's  use it, along with our new for look skills, to populate a dictionary with keys equal to each food, and values equal to the price.  As iterate through the items, keep track of the total cost of the items.


```python
# your code here. Fill in the code
groceries = None
total_cost = 0

for fill_in, fill_in in zip(fill_in, fill_in):
    '''
    Your code here:
    Add to key value pairs to dictionary
    Add to the cost of each item tot he total cost
    '''
print(groceries)
print(total_cost)


```


      File "<ipython-input-12-f8745ac5c317>", line 5
        for <fill_in>, <fill_in> in zip(<fill_in>, <fill_in>):
            ^
    SyntaxError: invalid syntax



So let's now add the total grocery bill at the end:


```python
sum(groceries.values()) == total_cost
```




    True



Does this look reasonable?

What if you only had $25? 

How can you build it out to stop adding items when the total is over $25?

### While, break, and continue
We were just introduced to while loops


```python
i = 1
while i < 6:
    print(i)
    i += 1
    
```

    1
    2
    3
    4
    5


### Knowledge check:
What would happen to the above code if we remove i += 1


```python
# Write your answer here
```

- What is break and continue?
- Are they different? How?
- Run the following code:


```python
i = 0
while i < 6:
    i += 1
    if i == 3:
        print("foo")
        
    print(i)
```

    1
    2
    foo
    3
    4
    5
    6


When a while loop includes continue, as soon as continue is encountered, we return to the top of the loop.

Before running this code, think about what the output will be:


```python
i = 0
while i < 6:
  i += 1
  if i == 3:
    print("foo")
    continue
  print(i)
```

    1
    2
    foo
    4
    5
    6


Why is the output different?

It stopped at foo, why?

We can also include `breaks` in for-loops.

When the code encounters break, we exit out of the while loop


```python
i = 0
while i < 6:
  i += 1
  if i == 3:
    break
print('Three is my limit')
```

    Three is my limit


What would we use to **stop** the for loop if the total reached $25?  
In other words, when you print out total_cost after exiting the loop, the value is less than 25


```python
# Take 2 minutes to code your answer below
groceries = {}
total_cost = 0

for i, c in zip(items, cost):
    "your code here"
    pass

print(groceries)
print(total_cost)
print(sum(groceries.values()))
```

    {}
    0
    0


What if we wanted to use continue to skip items that cost more than 10 dollars and break to stop the program if the total is more than 25 dollars.


```python
# Your code here
```

### Try and Except

Suppose we know our list of prices has some values which are not floats.



```python
items = ['cheese', 'whole milk', 'kefir', 'tofu four-pack', 
         'kale', 'oranges', 'ham', 'ben & jerry\'s']
cost = [{2.79: 'two for one'}, 3.42, 4.50, 12.00, 2.75, 3.64, 25.00, 5.29]
```

If we run our code, we encounter an error


```python
groceries = {}
total_cost = 0

for i, c in zip(items, cost):
    if c > 10:
        continue
    if total_cost + c >= 25.0:
        print(i)
        break
    print(i)
    groceries[i] = c
    total_cost += c
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-27-462b18880df7> in <module>
          3 
          4 for i, c in zip(items, cost):
    ----> 5     if c > 10:
          6         continue
          7     if total_cost + c >= 25.0:


    TypeError: '>' not supported between instances of 'dict' and 'int'


We can maneuver around this error try and except statements


```python
groceries = {}
total_cost = 0

for i, c in zip(items, cost):
    try:
        if c > 10:
            continue
        if total_cost + c >= 25.0:
            print(i)
            break
        print(i)
        groceries[i] = c
        total_cost += c
    except TypeError:
        print(f'Not numeric type: {c}')
```

    Not numeric type: {2.79: 'two for one'}
    whole milk
    kefir
    kale
    oranges
    ben & jerry's


We could run the same code without the TypeError specification.  But that goes against one of the Python tenents 



```python
import this
```

    The Zen of Python, by Tim Peters
    
    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!


**Errors should never pass silently**

## Practice with nested dictionaries

Here is a more robust shopping list of nested dictionaries:



```python
shopping_dict = {'Groceries': {'ben & jerrys': 5.29, 'cheese': 2.79,'ham': 25.0, 'kale': 2.75,'kefir': 4.5,'oranges': 3.64,'tofu four-pack': 12.0,'whole milk': 3.42},
                 'House supplies': {'cheese': 2.79,'toilet paper pack': 16.50, 'clorox spray': 6.43, 'kleenex': 2.50,},
                 'Pet supplies': {'cheese': 2.79,'Taste of the Wild': 65.20, 'squeaky toy': 4.50, 'duck feet': 8.45}}

```

Let's write some code to print out each grocery list with its total.

_Hint_

- use [this link](https://pyformat.info/#number) for help in formatting the total to two decimal places


```python
# your code here
```

# A complete function

Finally, let's use our budding knowledge of functions to write a robust function that will take any nested dictionary of items, costs, and print out your shopping list, stopping when the total cost gets to high, and telling you the average cost per item in your cart.


```python
def shopping_list_manager(nested_items_costs, price_limit):
    '''
    Function iterates through the lists of dictionaries, 
    adds items to a list until the price limit is reached
    then prints out the shopping list
    and average cost per item  
    '''
```


```python
shopping_list_manager(shopping_dict, 50)
```

    {'ben & jerrys': 5.29, 'cheese': 2.79, 'ham': 25.0, 'kale': 2.75, 'kefir': 4.5, 'oranges': 3.64}
    49.55
    Average cost: 8.26



```python

```
