Tags: #tech/language/python 

[[Python Standard Type Hierarchy]]

## Import
- Apart from import statement, the following can be used
	- `importlib.import_module()`
	- `__import__()`
- **modules** are of only 1 kind
	- **packages** are created to differentiate and have hierarchy
	- package is a module with `__path__` attribute
- **regular** package
	- uses `__init__.py` file in the directory
- **namespace** package
	- doesn't use `__init__.py` file
	- performs search for **portions** in zip files, network, or virtual modules
- For any given package like `foo.bar.baz`, packages will be imported in following order:
	- `foo`, `bar`, `baz`
- import mechanism
	- `sys.modules`
		- mapping that acts as a cache for previously imported modules
		- `foo`, `foo.bar`, `foo.bar.baz` will have separate keys
	- **loaders**
		- actually load the module
	- **finders**
		- implementations are called **importers**
		- return **module spec** when they can resolve a import
			- module spec will contain **loader**
		- import hooks
			- meta hooks
				- add finders to `sys.meta_path`
				- overrides `sys.path` processing
				- Default Finders
					- first: built in modules
					- second: frozen modules
					- third: import path
			- import hooks
				- add finders to `sys.path_hooks`
				- part of `sys.path` processing
	- Order of checking
		- `sys.modules`, 
		- `sys.meta_path`, 
		- `sys.path_hooks`

## Data and Expressions

### format
```format(‘hello’,’.<30’)```
Take the chars ‘hello’, print ‘.’ chars on the left side, such the entire string is 30 chars.

### explicit joining
Program lines can span multiple physical lines. In order to explicitly join them, use the ```\``` character. 

### keyboard input
```line = input(‘What is your age?’)```
This always returns a String.

### operators
```25//10``` is truncating division which gives answer 2
```2**3``` = 8, exponentiation

## Control Structures

### membership operators in and not in
```python
10 in (10,210,30)
'Dr.' in 'Dr. Mallapur'
20 not in (34,21,56)
```
All return ```True```

### boolean operators
```and or not```

### Conditions
```
if grade>= 90:
	print(‘A’)
elif grade>=80:
	print(‘B’)
else:
	print(‘C)
```
No braces, use indentation.
**header**: keyword to :
**suite**: statements following a header
**clause**: header + suite

### Loops
##### while
```
while condition:
	suite
```

## Collections

**Containers**
- Objects that contain reference to other objects as their values. 
- Dictionaries, tuples, lists.

### List
linear data structure, variable length, mixed-typed, mutable, zero-based indexing.

```
lst = [1,2,3]
lst = [1, 2, ‘jmd’]
lst[2]
del lst[0]
lst.insert[0, 'mango']
lst.append['banana']
lst.sort()
lst.reverse()
```

### Tuple
same as list, but immutable.
```
tpl = (1,'jmd',4)
tpl = ()
tpl = (1,)
```

### String
Also considered a sequence.

### Sequence operations in Python
|               | Operation          | String                | Tuple                     | List                      |
| :------------ | :----------------- | :-------------------- | :------------------------ | :------------------------ |
|               |                    | ```s=‘hello’ w='!'``` | ```s=(1,2,3,4) w=(5,6)``` | ```s=[1,2,3,4] w=[5,6]``` |
| length        | ```len(s)```       | 5                     | 4                         | 4                         |
| select        | ```s[0]```         | h                     | 1                         | 1                         |
| slice         | ```s[1:4]```       | ’ello’                | (2,3,4)                   | [2,3,4]                   |
|               | ```s[1:]```        | ’ello’                | (2,3,4)                   | [2,3,4]                   |
| count         | ```s.count(‘e’)``` | 1                     | 0                         | 0                         |
|               | ```s.count(4)```   | _error_               | 1                         | 1                         |
| index         | ```s.index(‘e’)``` | 1                     | --                        | --                        |
|               | ```s.index(3)```   | --                    | 2                         | 2                         |
| membership    | ```’h’ in s```     | True                  | False                     | False                     |
| concatenation | ```s+w```          | ’hello!’              | (1,2,3,4,5,6)             | [1,2,3,4,5,6]             |
| minimum       | ```min(s)```       | ’e’                   | 1                         | 1                         |
| maximum       | ```max(s)```       | ’o’                   | 4                         | 4                         |
| sum           | ```sum(s)```       | _error_               | 10                        | 10                        |

### Nested lists
```
class_grades = [[10,20,30], [11,22,33]]
class_grades[1][0]
```

### For loop
```
for k in sequence:
	suite
	
for k in range(5,19):
	suite
	
for k in range(len(seq)):
	print(seq[k])
```

### List comprehensions
```[expression for x in sequence condition]```
```[x**2 for x in [1,2,3]]``` gives ```[1,4,9]```
```[x for x in [2,3,4,5] if x>2]``` gives ```[3,4,5]```
```[ch for ch in ‘hello’ if ch in [‘a’,’e’,’i’,’o’,’u’]]``` gives ```[‘e’,’o’]```

## Functions

_program routine_ == _function_
_formal parameters_ == _parameters_
_actual arguments_ == _arguments_

### Value returning
```
def sum(a,b):
	return a+b

print(sum(1,2))
```
Will print 3

### Non Value returning
```
def sumnvr(a,b):
	a+b

print(sumnvr(1,2))
```
Will print ```None``` which is the default return value.

### mutable vs. immutable
Integers, Floats, Booleans, Strings, tuples are immutable. Passing them to functions that modify their arguments will not cause the change to retain outside the function call. Pass by value.
Lists are mutable. Passing them to a function that modifies its arguments will retain the change outside the function call. Pass by reference.

### positional arguments and keyword arguments
Consider
```python  
def volume(length, breadth, height):
	return length * breadth * height	
	
l=12, b=5, h=10
```

Call with positional arguments. Needs to be in order of formal parameters.
```python
volume(l, b, h)
```

Call with keyword arguments. Need not be in order of formal paramters as you are specifying each argument explicitly.
```python
volume(breadth=b, height=h, length=l)
```

A mixed call can be made but the keyword arguments must come at the end.
```python
volume(l, height=h, breadth=b)
```

### default arguments
Default arguments can be defined on the formal parameters at the end of a definition.
```python
def volume(len, brd, hght=20)
	return len * brd * hght

volume(10,12,5)
volume(10,12)
```

## Objects
### reference comparisons
2 references can be compared 
using ```id()``` as ```id(varA) == id(varB)``` 
or 
using the ```is``` operator as ```varA is varB```.

### list()
```
lstA=[10,20,30]
lstB=lstA
lstB is lstA == true

lstB=list(lstA)
lstB is lstA == false
```

#### shallow copy
Using list() on nested lists will not create different copies of the nest lists. Check diagram on _p214 of Charles Dierbach_.

## Modular Design
### Documentation
```python
def funcName1(varA,varB):
	“””This is the function’s documentation.”””

print(funcName1.__doc__)
```

### Import
In Python, modules are .py files that contain functions and code. They can be imported in another file by using the ```import moduleFileName``` command.

When a file is run, it is assigned the ```__main__``` identifier.

If 2 imported modules contain the same function, use the fully qualified name as ```module_name.function_name()```

To import everything in a module use the ```import``` command.
```import moduleName```

To import specific identifiers from a module, use the following form
```python
from moduleName import functionA
from moduleA import functionA as funcA
from moduleA import *
```

### private
- All variables inside a Python module are public. 
- Double underscore before a variable name insists that such variables are meant to be private and should not be referenced. This means that they will be imported when the ```import moduleName``` form of import is used.
	- If the ```from moduleName import *``` form of import is used then all variables with the double underscore prefix are not imported.

### module loading
1. current working directory
2. `PYTHONPATH`
3. Python installation-specific path
4. `ImportError` Exception

- When a module .py is imported
	- it is compiled into a .pyc and used. 
	- The next time it is imported, the .pyc is reused until a code change is detected.

### dir()
The ```dir()``` function allows to see the namespace of the main module. By default we have
```
__builtins__  __docs__  __name__  __package__
```

### Active namespaces
At any given time, any of the three namespaces may be active:
1. built_in: this is the Python built in namespace
2. global: this is the main module’s global variable set
3. local: this the namespace of the executing function at that time

## Text Files

#### Reading
```
infile = open('fileA.txt', 'r');
for line in infile:
	print(line)

infile.close()	
```

#### Writing
```
outfile = open('fileB.txt', 'w')
outfile.write('initial line')
outfile.close

outfile = open('fileB.txt', 'a')
outfile.write('appended line')
outfile.close
```

## Strings 
### String traversal

```
for chr in str:
	print(chr)
```

### String methods
For list of methods refere to _pg298 Charles Dierbach_

```str.strip(w)``` will remove w if it appears leading or trailing.

### Unicode
```
strB = r'abc'
strU = u'abc'
```
strB is a byte string. strU is a Unicode string.

## Exception handling

```
raise ValueError('something went wrong')

try:
	try suite
except ValueError:
	suite for handling ValueErrors

try:
	try suite
except ValueError as error:
	print(error)
	
try:
	try suite
except:
	suite to handle any failure

try:
	try suite
except Exception as e:
	suite to handle all Exception types
```

## Dictionaries and Sets

### Dictionary
- These are associative data structures similar to maps. 
- Mutable, variable length. 
- The keys are always immutable objects 
	- which means tuples can be used as keys but not lists.

```python
daily_temp = {
'sun' : 10,
'mon' : 20 
}

daily_temp['sun']
```

#### using a constructor for dicts
```python
s=[[‘a’, 1], [‘b’, 2]]
s_dict = dict(s)
```

#### check if key is present in dict
```python
'a' in s_dict
```

### Set
- Mutable, non-duplicate  
- unordered elements
- provided mathematical set operations
- ```frozenset``` is the immutable variant

```python
s_set = {1,2,3}
s_set = set([1,2,3])
s_set = frozenset([1,2,3])
```

```A | B``` : Union
```A & B``` : Intersection
```A - B``` : Difference
```A ^ B``` : Symmetric difference, in A or B but not in both

## Data Structure Syntax Recap
```[,]``` is for list
```(,)``` is for tuple
```{:,}``` is for dict
```{,}``` is for set

## Classes

```python
class Fraction(object):
	def __init__(self, num, den):
		self.__num = num
		self.__den = den
		self.reduce()
	
	def getNum(self):
		return self.__num
	
	def setNum(self, value):
		self.__num = value
```

### private
members are indicated as private by prefixing double underscores.
```
obj = SomeClass()
obj.__varA gives error
obj._SomeClass.__varA allows access
```

### Special methods
| method               | use                                       |
| :------------------- | :---------------------------------------- |
| ```__init__(self)``` | constructor                               |
| ```__str__(self)```  | called when ```print``` is used           |
| ```__repr__(self)``` | called when Python console wants to print |

### Operator overloading
| Operator | Method Used                |
| :------- | :------------------------- |
| ```+```  | ```__add__(self, right)``` |
| ```-```  | ```__sub__(self, right)``` |
| ```*```  | ```__mul__(self, right)``` |
| ```-```  | ```__neg__(self)```        |
| ```<```  | ```__lt__(self, right)```  |
| ```<=``` | ```__le__(self, right)```  |
| ```>```  | ```__gt__(self, right)```  |
| ```>=``` | ```__ge__(self, right)```  |
| ```=```  | ```__eq__(self, right)```  |
| ```!=``` | ```__ne__(self, right)```  |

### Inheritance and Polymorphism
```python
## object here means that Shape extends the object class
class Shape(object):
	def __init__(self, x, y):
		self.__x = x
		self.__y = y
		
	def move(self, x, y):
		"""unimplemented"""
		raise NotImplementedError("not impl")
		
	def calcArea(self):
		"""unimplemented"""
		raise NotImplementedError("not impl")


## Shape here means Circle extends the Shape class
class Circle(Shape):
	def __init__(self, x, y, r):
		Shape.__init__(self, x, y)
		self.__r = r
	
	def move(self, x, y):
		## some code
	
	def calcArea(self):
		## some code

		
class Triangle(Shape):
	def __init__(self, x, y, s):
		Shape.__init__(self, x, y)
		self.__s = s
	
	def move(self, x, y):
		## some code
	
	def calcArea(self):
		## some code
		

figureIn = input("Circle or Triangle?")
fig = None
if figureIn.lower() == "circle":
	fig = Circle(0, 0, 5)
elif figureIn.lower() == "triangle":
	fig = Triangle(0, 0, 5)

fig.move(10,10)
fig.calcArea()
```

## Databases

```python
import cx_Oracle

conn_str = u'user/password@host:port/service'
conn = cx_Oracle.connect(conn_str)
cur = conn.cursor()
cur.execute(u'select * from fgt_site_master')

for row in cur:
	print row[0], '|', row[1]

cur.close()
conn..close()
```


# References
- [Lexical Analysis](https://docs.python.org/3/reference/lexical_analysis.html)
	- indentation rules
	- variable naming rules
- 