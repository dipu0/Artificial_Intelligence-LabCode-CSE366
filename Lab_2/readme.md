# Float


```python
1/3
```




    0.3333333333333333




```python
print(format(1/3,'0.2f'))
```

    0.33
    


```python
import math
```


```python
print(format(math.pi,'.12f'))
```

    3.141592653590
    


```python
print(format(math.pi,'.12g'))
```

    3.14159265359
    


```python
2**52<=2**56//10 <2**53
```




    True




```python
2**52
```




    4503599627370496



# Starings


```python
season ="winter is coming"
```


```python
length = len(season )
```


```python
length 
```




    16




```python
last = season[length -3]
last
```




    'i'




```python
middle = season[length  - 8]
middle
```




    's'



# Loop


```python
for char in season:
    print(char)
```

    w
    i
    n
    t
    e
    r
     
    i
    s
     
    c
    o
    m
    i
    n
    g
    


```python
i=0
while(i < length):
    print (season [i])
    i+=1
```

    w
    i
    n
    t
    e
    r
     
    i
    s
     
    c
    o
    m
    i
    n
    g
    


```python
s1 = "CSE366 Lab Time"
for x in s1.split():
    print (x)
```

    CSE366
    Lab
    Time
    

# String Slices


```python
print(season [:6])
print(season [6:])
```

    winter
     is coming
    


```python
counter = 0
for x in season:
      counter +=1
print(counter)
```

    16
    

#


```python
new = season.upper()
new
```




    'WINTER IS COMING'




```python
cricket = ' BD beat Aus'
cricket.strip()
print(cricket)
```

     BD beat Aus
    


```python
a=[12,10,20,30]
a
```




    [12, 10, 20, 30]




```python
type(a)
```




    list




```python
a[2]='50'
a
```




    [12, 10, '50', 30]




```python
mixed = ['Rahat', 'Shamim', "Arif",10,20,30]
mixed
```




    ['Rahat', 'Shamim', 'Arif', 10, 20, 30]




```python
nested = ['Arif','Sagor',[10,20,30],'EWU','AUST','BUET','DU']
nested
```




    ['Arif', 'Sagor', [10, 20, 30], 'EWU', 'AUST', 'BUET', 'DU']




```python
for i in nested:
    print(nested)
```

    ['Arif', 'Sagor', [10, 20, 30], 'EWU', 'AUST', 'BUET', 'DU']
    ['Arif', 'Sagor', [10, 20, 30], 'EWU', 'AUST', 'BUET', 'DU']
    ['Arif', 'Sagor', [10, 20, 30], 'EWU', 'AUST', 'BUET', 'DU']
    ['Arif', 'Sagor', [10, 20, 30], 'EWU', 'AUST', 'BUET', 'DU']
    ['Arif', 'Sagor', [10, 20, 30], 'EWU', 'AUST', 'BUET', 'DU']
    ['Arif', 'Sagor', [10, 20, 30], 'EWU', 'AUST', 'BUET', 'DU']
    ['Arif', 'Sagor', [10, 20, 30], 'EWU', 'AUST', 'BUET', 'DU']
    

# if_else


```python
if case condition:
    print
elif condition:
    action
else:
    
```


```python
if True:
    print("The mornig was very charming")
```

    The mornig was very charming
    


```python
a= False
if a:
    print ('a: was true')
else:
    print('a: was not true')
```

    a: was not true
    


```python
loc = 'Bank'
if loc == 'Auto shop':
    print('Welcome to the Auto shop')
elif loc =='Bank':
    print('Welcome to the bank')
else:
    print('Where are you?')
```

    Welcome to the bank
    


```python
x=(1,2)
type(x)
```




    tuple




```python
numbers = (10,20,30)
x, y, z = numbers
```


```python
print(x,y,z)
```

    10 20 30
    

# Dictionary


```python
dictionary = {'EWU':'Dhaka','RU':'Rajshahi','CU':'Chottogram'}
dictionary
```




    {'EWU': 'Dhaka', 'RU': 'Rajshahi', 'CU': 'Chottogram'}




```python
dictionary['EWU']
```




    'Dhaka'



# set


```python
s={'a','b'}
s1= {'b','c'}
s.intersection(s1) ## Set unordered  collections. Set does not allow duplicate element.
```




    {'b'}



# Exercises

# CSE366 Lab 2 Exercises

## exercise 1
Write a program in Python to find the root of a quadratice
equation.


```python
#quadratic equation ax**2 + bx + c = 0

from math import sqrt
a=3
b=10
c=8
r = b**2 - 4*a*c

#when number of roots 2
if r > 0:
    root1 = (((-b) + sqrt(r))/(2*a))     
    root2 = (((-b) - sqrt(r))/(2*a))
    print("Number of roots is 2 :","X1: ",root1," X2",root2)
#when number of roots 1
elif r == 0:
    root = (-b) / 2*a
    print("Root: ", root)
#when number of roots 0
else:
    print("No roots")
```

    Number of roots is 2 : X1:  -1.3333333333333333  X2 -2.0
    

## exercise 2
Write code to perform grade computation


```python
Numerical_Scores= 96
if (97 <= Numerical_Scores <= 100):
    print(" You have obtained Grade A+ = 4.00 ")
elif  (90 <= Numerical_Scores < 97):
    print(" You have obtained Grade A = 4.00 ")        
elif  (87 <= Numerical_Scores < 90):
    print(" You have obtained Grade A- = 3.70 ")         
elif  (83 <= Numerical_Scores < 87):
    print(" You have obtained Grade B+ = 3.30 ")          
elif  (80 <= Numerical_Scores < 83):            
    print(" You have obtained Grade B = 3.00 ")           
elif  (77 <= Numerical_Scores < 80):           
    print(" You have obtained Grade B- = 2.70 ")            
elif  (73 <= Numerical_Scores < 77):
    print(" You have obtained Grade C = 2.00 ")           
elif  (67 <= Numerical_Scores < 70):
    print(" You have obtained Grade C- = 1.70 ")
elif (63 <= Numerical_Scores < 67):
    print(" You have obtained Grade D+ = 1.30 ")
elif  (60 <= Numerical_Scores < 63):
    print(" You have obtained Grade D = 1.00 ")
elif ( 0 <= Numerical_Scores < 60):
    print(" You have obtained Grade F = 0.00 ")
else :
    print('Invalid Numerical Scores')

```

     You have obtained Grade A = 4.00 
    

## exercise 3
Given two numeric lists or tuples x_vals and y_vals of equal
length, compute their inner product uzing zip(). Additionally count
the number of even number in 0 to 99. Furthermore given pairs =
((4, 5), (6,7), (8,9)) count the number of pairs (x,y) such that a and b
are odd.

### part1


```python
x_vals = [0, 9, 3]
y_vals = [9, 3, 0]
inner_product=0
for x, y in zip(x_vals, y_vals):
    inner_product += x*y
print(inner_product)
```

    27
    

### part2


```python
count =0
for i in range(0,99):
    if i%2 == 0:
        count+=1
print(count)
```

    50
    

### part3


```python
pairs = ((4, 5), (6, 7), (9, 8))
count =0
for x, y in pairs:    
    if (x % 2 != 0 and y % 2 != 0) :
        count+=1
        print(x," ",y) #print(x," ",y)
print(count)
```

    0
    


```python
# CSE366 Lab 2 Exercises

## exercise 1
Write a program in Python to find the root of a quadratice
equation.

#quadratic equation ax**2 + bx + c = 0

from math import sqrt
a=3
b=10
c=8
r = b**2 - 4*a*c

#when number of roots 2
if r > 0:
    root1 = (((-b) + sqrt(r))/(2*a))     
    root2 = (((-b) - sqrt(r))/(2*a))
    print("Number of roots is 2 :","X1: ",root1," X2",root2)
#when number of roots 1
elif r == 0:
    root = (-b) / 2*a
    print("Root: ", root)
#when number of roots 0
else:
    print("No roots")

## exercise 2
Write code to perform grade computation

Numerical_Scores= 96
if (97 <= Numerical_Scores <= 100):
    print(" You have obtained Grade A+ = 4.00 ")
elif  (90 <= Numerical_Scores < 97):
    print(" You have obtained Grade A = 4.00 ")        
elif  (87 <= Numerical_Scores < 90):
    print(" You have obtained Grade A- = 3.70 ")         
elif  (83 <= Numerical_Scores < 87):
    print(" You have obtained Grade B+ = 3.30 ")          
elif  (80 <= Numerical_Scores < 83):            
    print(" You have obtained Grade B = 3.00 ")           
elif  (77 <= Numerical_Scores < 80):           
    print(" You have obtained Grade B- = 2.70 ")            
elif  (73 <= Numerical_Scores < 77):
    print(" You have obtained Grade C = 2.00 ")           
elif  (67 <= Numerical_Scores < 70):
    print(" You have obtained Grade C- = 1.70 ")
elif (63 <= Numerical_Scores < 67):
    print(" You have obtained Grade D+ = 1.30 ")
elif  (60 <= Numerical_Scores < 63):
    print(" You have obtained Grade D = 1.00 ")
elif ( 0 <= Numerical_Scores < 60):
    print(" You have obtained Grade F = 0.00 ")
else :
    print('Invalid Numerical Scores')


## exercise 3
Given two numeric lists or tuples x_vals and y_vals of equal
length, compute their inner product uzing zip(). Additionally count
the number of even number in 0 to 99. Furthermore given pairs =
((4, 5), (6,7), (8,9)) count the number of pairs (x,y) such that a and b
are odd.

### part1

x_vals = [0, 9, 3]
y_vals = [9, 3, 0]
inner_product=0
for x, y in zip(x_vals, y_vals):
    inner_product += x*y
print(inner_product)

### part2

count =0
for i in range(0,99):
    if i%2 == 0:
        count+=1
print(count)

### part3

pairs = ((4, 5), (6, 7), (9, 8))
count =0
for x, y in pairs:    
    if (x % 2 != 0 and y % 2 != 0) :
        count+=1
        print(x," ",y) #print(x," ",y)
print(count)
```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```
