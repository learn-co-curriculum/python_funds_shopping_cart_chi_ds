
## Python Fundamentals Part II

**Scenario:** Today we are going to build our knowledge about for loops and functions. Who has ever got to the cash register at costco, or whole foods, seen the total and asked "how did I spend that much?". Today we have a grocery list of items and prices, but we do not have infinite money (unfortunately), so we need to have a program that will look at our grocery list and help us manage our shopping and cost.

### Learning goals:

Today we will:
 - describe what a for loop does 
 - use a for loop with a dictionary
 - use `break` to adjust loop activity
 - use nested loops to navigate a nested dictionary
 - write a robust function that will take any nested dictionary of items, costs, and print out your shopping list, stopping when the total cost gets to high, and telling you the average cost per item in your cart.
 - introduce list comprehensions and lambda functions

Let's revisit what a for loop does. Here we have a list of items, and a separate list of costs. We are going to write a loop to print each item, it's cost, and the total of our grocery list.

```
items = ['cheese', 'whole milk', 'kefir', 'tofu four-pack', 'kale', 'oranges', 'ham', 'ben & jerry's']
cost = [2.79, 3.42, 4.50, 12.00, 2.75, 3.64, 25.00, 5.29]
```

![groc-cart](https://images.pexels.com/photos/1389103/pexels-photo-1389103.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260)

### For loops:
First, let's create a for-loop that prints each item in the list with "I need to buy: " item.

Let's make that a little nicer looking:

```
print("I need to buy: ")
for item in items:
   print(" - [ ] ", item)
```

Okay, we want to work through a dictionary, so what's one way to convert those two lists to a dictionary?

_Hint_: Check [this](https://www.w3schools.com/python/ref_func_zip.asp) documentation. 

So let's now add the total grocery bill at the end:

Does this look reasonable?

What if you only had $25? 

How can you build it out to stop adding items when the total is over $25?

### While, break, and continue
What does a while loop look like in Python?

- What is break and continue?
- Are they different? How?
- Run the following code:

How does the code above work?

Now run this code:

Why is the output different?

It stopped at foo, why?

We can also include `breaks` in for-loops.

What would we use to **stop** the for loop if the total reached $25?

What if we wanted to use continue to skip items that cost more than 10 dollars and break to stop the program if the total is more than 25 dollars.

### Try and Except

### Nested Loops

What do you expect to see? Why?

Here's a more complicated example, what is it doing?

Here is a more robust shopping list of nested dictionaries:
```
shopping_dict = {'Groceries': {'ben & jerrys': 5.29, 'cheese': 2.79,'ham': 25.0, 'kale': 2.75,'kefir': 4.5,'oranges': 3.64,'tofu four-pack': 12.0,'whole milk': 3.42},
                 'House supplies': {'toilet paper pack': 16.50, 'clorox spray': 6.43, 'kleenex': 2.50,},
                 'Pet supplies': {'Taste of the Wild': 65.20, 'squeaky toy': 4.50, 'duck feet': 8.45}}
```

write the nested for loops to print out each grocery list with its total

_Hint_

- use [this link](https://pyformat.info/#number) for help in formatting the total to two decimal places

### Functions

**Built-in functions** <br>
Many useful functions are already built into Python:<br>

`print()`: print the given string or variable's value<br>
`type()`: returns the datatype of the argument<br>
`len()`: returns the length of an array<br>
`sum()`: returns the sum of the array's values<br>
`min()`: returns the smallest member of an array <br>
`max()`: returns the largest member of an array<br>


**Writing your own functions**

```
def sayHello():
  print("Hello!")
```
How do we run it?

```
sayHello()
```

Let's talk about arguments or parameters. Let's say we want to make this function more dynamic and print out whatever we want! How would we do that?
```
def shout(phrase):
  print(phrase + "!!!")
shout("oh hai")
```

What if we don't pass in an argument? What happens?
Maybe we can establish a default value for the argument in case it isn't passed in.

```
def shout(phrase = "oh hai"):
  print(phrase + "!!!")

shout()
shout("bye")
```

What if we wanted to run a function, take it's output and put it in to another function?

```
def addOne(number):
  return number + 1

def timesFive(number):
  return number * 5

numberPlusOne = addOne(1)
answer = timesFive(numberPlusOne)
print(answer)
```

What will the above code return?

Adapt your shopping list nested for-loop to be wrapped in a function you could call on any shopping list of nested dictionaries.

### Mathematical Notation and Measures of Central Tendency 

median vs mode vs mean<br>
What's the difference?


`samp_list = [1,1,1,1,2,2,2,3,3,10,44]`

How could you write a for loop to calculate the mean?

### Integration

adapt your function to do the following:
- stop the nested loop if a grocery total goes over $30
- print out the average cost of per item in your cart

## Bonus


### List comprehensions

List comprehensions are faster than for loops, and generally more legible once you get used to the syntax.  

    ''' 
    Input:
    
    list1 = [1,2,3,4,5]
    
    list1_comp = [number**2 for number in list1]
    
    print(list1_comp)
    
    Output:
    [1,4,9,16,25]
    
    '''

#### Lambda functions

Lambda functions are unamed.  They don't have to be defined before hand. They can be defined on the run. 
