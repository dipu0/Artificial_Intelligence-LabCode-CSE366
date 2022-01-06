```python
pip install sympy
```

    Requirement already satisfied: sympy in c:\programdata\anaconda3\lib\site-packages (1.8)
    Requirement already satisfied: mpmath>=0.19 in c:\programdata\anaconda3\lib\site-packages (from sympy) (1.2.1)
    Note: you may need to restart the kernel to use updated packages.
    


```python
pip install kanren
```

    Requirement already satisfied: kanren in c:\programdata\anaconda3\lib\site-packages (0.2.3)
    Requirement already satisfied: unification in c:\programdata\anaconda3\lib\site-packages (from kanren) (0.2.2)
    Requirement already satisfied: toolz in c:\programdata\anaconda3\lib\site-packages (from kanren) (0.11.1)
    Requirement already satisfied: multipledispatch in c:\programdata\anaconda3\lib\site-packages (from kanren) (0.6.0)
    Requirement already satisfied: six in c:\programdata\anaconda3\lib\site-packages (from multipledispatch->kanren) (1.15.0)
    Note: you may need to restart the kernel to use updated packages.
    

## Create a JSON file named relationships to show parent-child relation:

{
"father":
[
{"John": "William"},
{"John": "David"},
{"John": "Adam"},
{"William": "Chris"},
{"William": "Stephanie"},
{"David": "Wayne"},
{"David": "Tiffany"},
{"David": "Julie"},
{"David": "Neil"},
{"David": "Peter"},
{"Adam": "Sophia"}
],
"mother":
[
{"Megan": "William"},
{"Megan": "David"},{"Megan": "Adam"},
{"Emma": "Stephanie"},
{"Emma": "Chris"},
{"Olivia": "Tiffany"},
{"Olivia": "Julie"},
{"Olivia": "Neil"},
{"Olivia": "Peter"},
{"Lily": "Sophia"}
]
}


```python
import json
from kanren import Relation, facts, conde, run, eq, var
```

## Define a function to check if x is the parent of y.
We will use the logic that if x is
the parent of y, then x is either the father or the mother.


```python
# Check if 'x' is the parent of 'y'
def parent(x, y):
    return conde([father(x, y)], [mother(x, y)])
```

## Define a function to check if x is the grandparent of y.
We will use the logic that if
x is the grandparent of y, then the offspring of x will be the parent of y:


```python
# Check if 'x' is the grandparent of 'y'
def grandparent(x, y):
    temp = var()
    return conde((parent(x, temp), parent(temp, y)))
```

## Define a function to check if x is the sibling of y.
We will use the logic that if x is the
sibling of y, then x and y will have the same parents. Notice that there is a slight
modification needed here because when we list out all the siblings of x, x will be
listed as well because x satisfies these conditions. So, when we print the output,
we will have to remove x from the list.


```python
# Check for sibling relationship between 'a' and 'b'
def sibling(x, y):
    temp = var()
    return conde((parent(temp, x), parent(temp, y)))
```

## Define a function to check if x is y's uncle.
We will use the logic that if x is y's uncle,
then x grandparents will be the same as y's parents. Notice that there is a slight
modification needed here because when we list out all the uncles of x, x's father will
be listed as well because x's father satisfies these conditions. So, when we print the
output, we will have to remove x's father from the list.


```python
# Check if x is y's uncle
def uncle(x, y):
    temp = var()
    return conde((father(temp, x), grandparent(temp, y)))
```

## Define the main function and initialize the relations father and mother:


```python
if __name__=='__main__':
    father = Relation()
    mother = Relation()
```

## Load the data from the relationships.json file:


```python
with open('lab_6.json') as f:
    d = json.loads(f.read())
```

## Read the data and add it to the fact base:


```python
for item in d['father']:
    facts(father, (list(item.keys())[0], list(item.values())[0]))
    
for item in d['mother']:
    facts(mother, (list(item.keys())[0], list(item.values())[0]))
```

## Define the variable x:


```python
x = var()
```

We are now ready to ask some questions and see if the solver can come up with the
right answers.

### Let's ask who John's children are:


```python
# John's children
name = 'John'
output = run(0, x, father(name, x))
print("\nList of " + name + "'s children:")
for item in output:
    print(item)
```

    
    List of John's children:
    William
    Adam
    David
    

### Who is William's mother?


```python
# William's mother
name = 'William'
output = run(0, x, mother(x, name))[0]
print("\n" + name + "'s mother:\n" + output)
```

    
    William's mother:
    Megan
    

### Who are Adam's parents?


```python
# Adam's parents name = 'Adam'
output = run(0, x, parent(x, name))
print("\nList of " + name + "'s parents:")
for item in output:
    print(item)
```

    
    List of William's parents:
    John
    Megan
    

### Who are Wayne's grandparents?


```python
# Wayne's grandparents name = 'Wayne'
output = run(0, x, grandparent(x, name))
print("\nList of " + name + "'s grandparents:")
for item in output:
    print(item)
```

    
    List of William's grandparents:
    

### Who are Megan's grandchildren?


```python
# Megan's grandchildren
name = 'Megan'
output = run(0, x, grandparent(name, x))
print("\nList of " + name + "'s grandchildren:")
for item in output:
    print(item)
```

    
    List of Megan's grandchildren:
    Chris
    Tiffany
    Sophia
    Stephanie
    Wayne
    Neil
    Peter
    Julie
    

### Who are David's siblings?


```python
# David's siblings
name = 'David'
output = run(0, x, sibling(x, name))
siblings = [x for x in output if x != name]
print("\nList of " + name + "'s siblings:")
for item in siblings:
    print(item)
```

    
    List of David's siblings:
    William
    Adam
    

### Who are Tiffany's uncles?


```python
# Tiffany's uncles
name = 'Tiffany'
name_father = run(0, x, father(x, name))[0]
output = run(0, x, uncle(x, name))
output = [x for x in output if x != name_father]
print("\nList of " + name + "'s uncles:")
for item in output:
    print(item)
```

    
    List of Tiffany's uncles:
    William
    Adam
    

### List all of the spouses in the family:


```python
# All spouses
a, b, c = var(), var(), var()
output = run(0, (a, b), (father, a, c), (mother, b, c))
print("\nList of all spouses:")
for item in output:
    print('Husband:', item[0], '<==> Wife:', item[1])
```

    
    List of all spouses:
    Husband: William <==> Wife: Emma
    Husband: David <==> Wife: Olivia
    Husband: John <==> Wife: Megan
    Husband: Adam <==> Wife: Lily
    
