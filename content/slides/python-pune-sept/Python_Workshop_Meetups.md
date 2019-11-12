## Hidden Secrets of Python 

## Get a copy of this notebook [here](https://bit.ly/python-meetups-sept)


## F-Strings 

PEP 498 introduced a new string formatting mechanism known as Literal String Interpolation or more commonly as F-strings

Why F-Strings?
- They are fast.
- They can evaluate expressions.


```
a = 10 
b = 20

print(f"{a + b}")
```

## Yield 

The yield statement suspends function’s execution and sends a value back to caller, but retains enough state to enable function to resume where it is left off. It is used in Python generator functions.





```
def foo(bar):
  yield bar
  print(f"Resuming execution after returning {bar}")
  yield bar + 1
  print(f"Resuming execution after returning {bar + 1}")
  yield bar + 2
  print(f"Resuming execution after returning {bar + 2}")

values_returned = foo(10)

for value in values_returned:
  print(value)
```

## Context Managers

Context Managers are used to manage resources which includes file pointers, variables etc. The scope of the variables is retained within the context.


```
 ''' 
 with open("file.txt","r") as f:
  data = f.read()
'''
class ContextManager(): 
    def __init__(self): 
        print('init method called') 
          
    def __enter__(self): 
        print('enter method called') 
        return self
      
    def __exit__(self, exc_type, exc_value, exc_traceback): 
        print('exit method called') 


with ContextManager() as manager: 
    print('with statement block') 

```

## Else Clauses on Loops

Python allows us to add else conditions to for/while loops as well.  If the for/while loop condition fails, then the else statement is executed. 


```

def find_index(to_search,target):
  flag = False
  index = int()
  for i,value in enumerate(to_search):
    if value == target:
      flag = True
      index = i
      break

  if flag:
    return index
  else:
     return -1 


my_list = ['Corey', 'Rick', 'John']
index_location = find_index(my_list, 'Steve')

print('Location of target is index: {}'.format(index_location))
```


```
def find_index(to_search, target):
  for i, value in enumerate(to_search):
    if value == target:
      break
  else:
    return -1
  return i


my_list = ['Corey', 'Rick', 'John']
index_location = find_index(my_list, 'Steve')

print('Location of target is index: {}'.format(index_location))
```

## Named Tuples

Named tuples are easy-to-create, lightweight object types. Named tuple instances can be referenced using object-like variable dereferencing or the standard tuple syntax. They can be used similarly to struct or other common record types, except that they are immutable.


```
from collections import namedtuple

Color = namedtuple('Color', ['red', 'green', 'blue'])

color = Color(red = 55,green = 155,blue = 255)
white = Color(255,255,255)

print(color.blue)
```

## Itertools - To Manage Looping Efficiently

Python has an extensive suite of iterators in its itertools module, which allow for memory efficient and faster looping. It is recommended that programmers should rely on these pre-defined iterators instead of hard-coding the logic by themselves.


```
from itertools import count, cycle, compress, groupby, permutations, combinations


## 1. Count 
print("Demonstration of count")
for i in count(10,2):
  print(i)
  if i == 30:
    break

# 2. Cycle
print("Demonstration of cycle")
iteration = 0 
for i in cycle("ABC"):
  print(i)
  iteration += 1
  if iteration == 5:
    break

# 3. Group By
print("Demonstration of Group by")
def get_state(person):
    return person['state']

people = [
    {
        'name': 'John Doe',
        'city': 'Gotham',
        'state': 'NY'
    },
    {
        'name': 'Jane Doe',
        'city': 'Kings Landing',
        'state': 'NY'
    },
    {
        'name': 'Corey Schafer',
        'city': 'Boulder',
        'state': 'CO'
    },
    {
        'name': 'Al Einstein',
        'city': 'Denver',
        'state': 'CO'
    },
    {
        'name': 'John Henry',
        'city': 'Hinton',
        'state': 'WV'
    },
    {
        'name': 'Randy Moss',
        'city': 'Rand',
        'state': 'WV'
    },
    {
        'name': 'Nicole K',
        'city': 'Asheville',
        'state': 'NC'
    },
    {
        'name': 'Jim Doe',
        'city': 'Charlotte',
        'state': 'NC'
    },
    {
        'name': 'Jane Taylor',
        'city': 'Faketown',
        'state': 'NC'
    }
]

person_group = groupby(people, get_state)

for group,values in person_group:
  print(group,[value['name'] for value in values])

# 4. Compress
print("Demonstration of compress")
values = compress("Meetups",[1,1,1,1,0,0,0])
print(list(values))

# 5. Permutations
print("Demonstration of permutations")

lst = [1,2,3]
for perm in permutations(lst,2):
  print(perm)


# 6. Combinations 
print("Demonstration of combinations")
name = "ABCD"

for comb in combinations(name,2):
  print(comb)

```

## One liner if else if else condition

Python allows a cleaner and shorthand syntax for defining if-else statements. 


```
a = 10
print('Even') if a % 2 == 0 else print('False')

```

## Swapping variables

Variable swapping can be done without the need of a third temporary variable.


```
a,b = 1,2
print(a,b)

a,b = b,a
print(a,b)
```

## Chained function call

Python allows a cleaner and shorthand syntax for defining chained else-if statements. 


```

def add(x,y):
  return x + y

def sub(x,y):
  return x - y

def mul(x,y):
  return x * y

x = 1

# Lengthy approach
if x == 1:
  print(add(10,20))
elif x == 2:
  print(sub(10,20))
elif x == 3:
  print(mul(10,20))
  
# Quick approach 
print((add if x == 1 else sub if x == 2 else mul)(10,20))

```

## Print an array with strings as one comma-separated string

The power of Python allows you to print a list to the standard I/O, with the choice of your own delimiter like a comma. 


```
row = ["1", "bob", "developer", "python"]
print(*row, sep=',')

```

## Enumerate

List enumeration can be done without the need of maintaining manual counter with the enumerate function. 


```
cities = ["London", "Paris", "New York"]

# Lengthy approach
count=0
for city in cities:
  print(count,city)
  count+=1

# Recommended approach
for count,city in enumerate(cities):
  print(count,city)
  
```

    0 London
    1 Paris
    2 New York
    0 London
    1 Paris
    2 New York


## Zip
Two or more iterables can be iterated in parallel with the zip function. 


```
roll_no = [101,102,103,104,105,106,107,108,109,110]
marks = [45,32,23,15,44]

# Lengthy approach
'''for i in range(len(roll_no)):
    r = roll_no[i]
    m = marks[i]
    #print(r,m)
   ''' 
# Recommended approach
for r,m in zip(roll_no,marks):
    print(r,m)
```

    101 45
    102 32
    103 23
    104 15
    105 44


## Hiding Your Source Code 

Since Python is built on C, the Python interpreter has the benefits that a C compiler has. Python code can be translated to a runnable binary with the .pyc file. The Python interpreter converts the .py file to a runnable binary in order to prevent recompilation of the code and save time in future. If the same python script is called again, the interpreter simply exectutes the precompiled .pyc file to save time. 


```bash 

chaitanya@meetups$ python3 -m py_compile foo.py

```

## GetPass Function 

Ever created a Python script that accepts passwords as input? The normal input() function in Python shows on the screen what you are typing. The GetPass function allows you to get passwords as input the UNIX style. 




```
from getpass import getpass 

username = input("Enter your username: ")
password  = getpass("Enter your password: ")

print(username,password,sep = '\n')
```

## HTTP Server 

Want to host your files or a static website? Python has a built in minimalistic HTTP Server useful for serving static content. It is fast and easy to use. 

```bash 

anushka@meetups$ python3 -m http.server 8001 

```

## Hiding Secrets & Keys with Enviroment variables 

Exposing your private keys or passwords in Python scripts is not a good idea, especially if you are uploading the code on some online repository. Secrets and keys should be stored in environment variables, which then Python can access through the <i> os </i> module. 

On a Linux/Mac machine - 

```bash

chaitanya@meetups$ nano .bash_profile 

```

Add a line to the .bash_profile file -
```bash 

export password="mypassword" 

```



```
import os 


print(os.environ.get("password"))
```

## Underscore placeholders

#### There are five underscore variable naming conventions used in Python 
- Single Leading Underscore: _var
- Single Trailing Underscore: var_
- Double Leading Underscore: __var
- Double Leading and Trailing Underscore: \__var\__
- Single Underscore: _


```
_x = 10 # 1. Variable is for internal use
class_ = 14 # 2. To use keywords as variable names
for_ = "Meetups" 

# 3. Acts as a sort-of private variable (Name-mangling)

class Base(object):
  def __init__(self): # Constructor 
    self.__foo = 7 

class Derived(Base):
  def __init__(self):
    super().__init__() # Calling the base class constructor
    self.__foo = 10 


s = Derived()
print("Value from derived class: ",s._Derived__foo)
print("Value from base class: ",s._Base__foo)

# 4. __var__ is reserved for internal Python magic methods and variables. Not recommended to be used by programmer.

# 5. Single underscore acts as useless variables by convention. It is also used as a temporary variable in Python REPL 

for _ in range(2):
  # Code 
  None 



```

## Secrets Module

Python has a module to generate secure random numbers. It uses the operating system's random number generator. 




```
import secrets 
  
token = secrets.token_hex(16) 
  
print(token)



```


```
  # Why the random module in Python is insecure 
  r1 = random.Random(31337)
  outputs = [r1.getrandbits(32) for _ in range(625)]
  
  mtr = MT19937Recover() # Mersenne Twister Breaker 
  r2 = mtr.go(outputs)
  
  print(r1.getrandbits(32) == r2.getrandbits(32))
```

## Shallow and Deep Copy 

In Python, assignment statements do not copy objects, they create bindings between a target and an object. When we use = operator user thinks that this creates a new object; well, it doesn’t. It only creates a new variable that shares the reference of the original object.


```
# Shallow copy 
l = [1,2,3,4,5]

p = l 

l[0] = 100 

print(p[0])
```

    100



```
# Deep copy 
import copy 

l = [1,2,3,4,5]

p = copy.deepcopy(l) # Creates a deep copy
q = list(l) # Creates a deep copy 

l[0] = 100 
print(p[0])
print(q[0])
```

    1
    1



```
a = [0 for i in range(5)]

mat = list()

for _ in range(5):
  mat.append(a) # Creates a shallow copy 

mat[1][1] = 10 

print(mat)

```

## Default Dictionary

Python allows us to preset dictionary values even if a given key does not exist in the dictionary. This can be done with defaultdict from collections module. 


```
import collections

data = {
    'Tom':33,
    'Jack':45,
    'Jill':32,
    'Mark':45,
    'Sam':38
}

# Lengthy way

if 'John' in data:
  print(data['John'])
else:
  print('Absent')
  
# Recommended way

print(data.get('John','Absent'))

# Recommended way

marks_data = collections.defaultdict(int)
print(marks_data['Tom'])

pass_data = collections.defaultdict(str)
print(pass_data['Tom'])

students_data = collections.defaultdict(lambda:'Absent')
students_data.update(data)

print(students_data['Jim'])
```

## Type Hinting

Type hinting is a Python programming convention that allows us to specify the return type & parameters of the function. This is a good coding practice that improves code readability. 


```
def headline_without_type(text, align=True):
    if align:
        return f"{text.title()}\n{'-' * len(text)}"
    else:
        return f" {text.title()} ".center(50, "o")


def headline_with_type(text: str, align: bool = True) -> str:
    if align:
        return f"{text.title()}\n{'-' * len(text)}"
    else:
        return f" {text.title()} ".center(50, "o")

      
print(headline_without_type("python type checking"))
print(headline_with_type("python type checking", False))

```

## == vs is
There are two ways in Python to check the equivalence of two variables. However there is a big difference between their compiler level implementation.  


```
list1 = [1,2,3]
list2 = list1
list3 = list(list1)

print(list1 == list2)
print(list1 == list3)

print(list1 is list2)
print(list1 is list3)
```

    True
    True
    True
    False


## Extended Iterable Unpacking

Extended iterable unpacking allows us to use star operator to gather items from an iterable as a list. 


```
a,b,c = [1,2,3]
print(a,b,c)

cities = ['London','Paris','New York','Boston','Jerusalem','California']
start,*route,end = cities

print(start)
print(route)
print(end)
```

    1 2 3
    London
    ['Paris', 'New York', 'Boston', 'Jerusalem']
    California


## Antigravity 

Python is not that boring! It is full of strange and interesting things that never stop surprising us. This is really one of them! 


```
import antigravity
```
