
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

Let's make that a little nicer looking:


We learned earlier how to use [zip](https://www.w3schools.com/python/ref_func_zip.asp).  Let's  use it, along with our new for look skills, to populate a dictionary with keys equal to each food, and values equal to the price.  As iterate through the items, keep track of the total cost of the items.


```python
groceries = {}
total_cost = 0

for i, c in zip(items, cost):
    groceries[i] = c
    total_cost += c
print(total_cost)
```

    59.39


So let's now add the total grocery bill at the end:

Does this look reasonable?

What if you only had $25? 

How can you build it out to stop adding items when the total is over $25?

### While, break, and continue
We were just introduced to while loops

### Knowledge check:
What would happen to the above code if we remove i += 1


```python
"""
The code would run forever, printing out a never ending string of i's
"""
```

- What is break and continue?
- Are they different? How?
- Run the following code:

When a while loop includes continue, as soon as continue is encountered, we return to the top of the loop.

Before running this code, think about what the output will be:

Why is the output different?

It stopped at foo, why?

We can also include `breaks` in for-loops.

When the code encounters break, we exit out of the while loop

What would we use to **stop** the for loop if the total reached $25?  
In other words, when you print out total_cost after exiting the loop, the value is less than 25


```python
groceries = {}
total_cost = 0

for i, c in zip(items, cost):
    if total_cost + c >= 25.0:
        print(i)
        break
    print(i)
    groceries[i] = c
    total_cost += c

print(groceries)
print(total_cost)
print(sum(groceries.values()))
```

    cheese
    whole milk
    kefir
    tofu four-pack
    kale
    {'cheese': 2.79, 'whole milk': 3.42, 'kefir': 4.5, 'tofu four-pack': 12.0}
    22.71
    22.71


What if we wanted to use continue to skip items that cost more than 10 dollars and break to stop the program if the total is more than 25 dollars.


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

print(groceries)
print(total_cost)
print(sum(groceries.values()))
```

    cheese
    whole milk
    kefir
    kale
    oranges
    ben & jerry's
    {'cheese': 2.79, 'whole milk': 3.42, 'kefir': 4.5, 'kale': 2.75, 'oranges': 3.64, "ben & jerry's": 5.29}
    22.39
    22.39


### Try and Except

Suppose we know our list of prices has some values which are not floats.


If we run our code, we encounter an error

We can maneuver around this error try and except statements

We could run the same code without the TypeError specification.  But that goes against one of the Python tenents 


**Errors should never pass silently**

## Practice with nested dictionaries

Here is a more robust shopping list of nested dictionaries:


Let's write some code to print out each grocery list with its total.

_Hint_

- use [this link](https://pyformat.info/#number) for help in formatting the total to two decimal places


```python
for shopping_list in shopping_dict:
    total = sum(shopping_dict[shopping_list].values())
    
    print('{:.2f}'.format(total))
```

    59.39
    28.22
    80.94


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
    
    total_cost = 0
    grocery_list = {}
    for g_list in nested_items_costs.keys():
        for item, cost in nested_items_costs[g_list].items():
            if total_cost + cost > price_limit:
                break
            else:
                grocery_list[item] = cost
                total_cost += cost
                
    print(grocery_list)
    print(total_cost)
    print(f"Average cost: {'{:.2f}'.format(total_cost/len(grocery_list))}")
    
```
