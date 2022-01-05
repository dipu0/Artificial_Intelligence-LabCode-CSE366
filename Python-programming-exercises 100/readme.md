# 100+ Python challenging programming exercises

### Question 1
### Level 1
Question:
Write a program which will find all such numbers which are divisible by 7 but are not a multiple of 5,
between 2000 and 3200 (both included).
The numbers obtained should be printed in a comma-separated sequence on a single line.

Hints: 
Consider use range(#begin, #end) method


```python
list = []
c=0
for x in range(1999,3201):
    if (x%7==0 and x%5!=0):
        c +=1
        list.append(x)
        
print( "Total number: ",c,"\n",list) 

        
        
  
```

    Total number:  138 
     [2002, 2009, 2016, 2023, 2037, 2044, 2051, 2058, 2072, 2079, 2086, 2093, 2107, 2114, 2121, 2128, 2142, 2149, 2156, 2163, 2177, 2184, 2191, 2198, 2212, 2219, 2226, 2233, 2247, 2254, 2261, 2268, 2282, 2289, 2296, 2303, 2317, 2324, 2331, 2338, 2352, 2359, 2366, 2373, 2387, 2394, 2401, 2408, 2422, 2429, 2436, 2443, 2457, 2464, 2471, 2478, 2492, 2499, 2506, 2513, 2527, 2534, 2541, 2548, 2562, 2569, 2576, 2583, 2597, 2604, 2611, 2618, 2632, 2639, 2646, 2653, 2667, 2674, 2681, 2688, 2702, 2709, 2716, 2723, 2737, 2744, 2751, 2758, 2772, 2779, 2786, 2793, 2807, 2814, 2821, 2828, 2842, 2849, 2856, 2863, 2877, 2884, 2891, 2898, 2912, 2919, 2926, 2933, 2947, 2954, 2961, 2968, 2982, 2989, 2996, 3003, 3017, 3024, 3031, 3038, 3052, 3059, 3066, 3073, 3087, 3094, 3101, 3108, 3122, 3129, 3136, 3143, 3157, 3164, 3171, 3178, 3192, 3199]
    

### Question 2
### Level 1
Question:
Write a program which can compute the factorial of a given numbers.
The results should be printed in a comma-separated sequence on a single line.
Suppose the following input is supplied to the program:
8
Then, the output should be:
40320

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.


```python
def fact(x):
    if x == 0:
        return 1
    return (x * fact(x - 1))

print("Enter the Number:")
x=int(input())
print(fact(x))
```

    Enter the Number:
    8
    40320
    

### Question 3
### Level 1
Question:
With a given integral number n, write a program to generate a dictionary that contains (i, i*i) such that is an integral number between 1 and n (both included). and then the program should print the dictionary.
Suppose the following input is supplied to the program:
8
Then, the output should be:
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64}

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.
Consider use dict()


```python
print("Enter the Number:")
n=int(input())
d=dict()
for i in range(1,n+1):
    d[i] = i*i

print(d)
```

    Enter the Number:
    8
    {1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64}
    

## Question 4
### Level 1

Question:
Write a program which accepts a sequence of comma-separated numbers from console and generate a list and a tuple which contains every number.
Suppose the following input is supplied to the program:
34,67,55,33,12,98
Then, the output should be:
['34', '67', '55', '33', '12', '98']
('34', '67', '55', '33', '12', '98')

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.
tuple() method can convert list to tuple



```python
sequence = input()
list = sequence.split(",")
tuple = list
print("List:",list,"\n","Tuple:", tuple)
```

     34,67,55,33,12,98
    List: [' 34', '67', '55', '33', '12', '98'] 
     Tuple: [' 34', '67', '55', '33', '12', '98']
    

## Question 5
### Level 1

Question:
Define a class which has at least two methods:
getString: to get a string from console input
printString: to print the string in upper case.
Also please include simple test function to test the class methods.

Hints:
Use __init__ method to construct some parameters


```python
class Input_Print_String(object):
    def __init__(self):
        self.string = ""
    def getString(self):
        self.string = input()
    def printString(self):
        print(self.string.upper())

strObject = Input_Print_String()
strObject.getString()
strObject.printString()

```

    hello!
    HELLO!
    

## Question 6
### Level 2

Question:
Write a program that calculates and prints the value according to the given formula:
Q = Square root of [(2 * C * D)/H]
Following are the fixed values of C and H:
C is 50. H is 30.
D is the variable whose values should be input to your program in a comma-separated sequence.
Example
Let us assume the following comma separated input sequence is given to the program:
100,150,180
The output of the program should be:
18,22,24

Hints:
If the output received is in decimal form, it should be rounded off to its nearest value (for example, if the output received is 26.0, it should be printed as 26)
In case of input data being supplied to the question, it should be assumed to be a console input. 



```python
import math
c = 50
h = 30
value = []
items = []
input_items = input()
input_items = input_items.split(',')


for x in input_items:
    items.append(x)

print("list: ",items)
for d in items:
    value.append(str(int(round(math.sqrt(2*c*float(d)/h)))))

print(','.join(value))
```

    100,150,180
    list:  ['100', '150', '180']
    18,22,24
    

## Question 7
## Level 2

Question:
Write a program which takes 2 digits, X,Y as input and generates a 2-dimensional array. The element value in the i-th row and j-th column of the array should be i*j.
Note: i=0,1.., X-1; j=0,1,¡­Y-1.
Example
Suppose the following inputs are given to the program:
3,5
Then, the output of the program should be:
[[0, 0, 0, 0, 0], [0, 1, 2, 3, 4], [0, 2, 4, 6, 8]] 

Hints:
Note: In case of input data being supplied to the question, it should be assumed to be a console input in a comma-separated form.



```python
input_str = input()
dimensions=[int(x) for x in input_str.split(',')]
rowNum=dimensions[0]
colNum=dimensions[1]
multilist = [[0 for col in range(colNum)] for row in range(rowNum)]

for row in range(rowNum):
    for col in range(colNum):
        multilist[row][col]= row*col

print(multilist)

```

    3,5
    [[0, 0, 0, 0, 0], [0, 1, 2, 3, 4], [0, 2, 4, 6, 8]]
    

## Question 8
## Level 2

Question:
Write a program that accepts a comma separated sequence of words as input and prints the words in a comma-separated sequence after sorting them alphabetically.
Suppose the following input is supplied to the program:
without,hello,bag,world
Then, the output should be:
bag,hello,without,world

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.


```python
items=[x for x in input().split(',')]
items.sort()
print(','.join(items))
```

    34,67,55,33,12,98
    12,33,34,55,67,98
    

## Question 9
### Level 2

Question£º
Write a program that accepts sequence of lines as input and prints the lines after making all characters in the sentence capitalized.
Suppose the following input is supplied to the program:
Hello world
Practice makes perfect
Then, the output should be:
HELLO WORLD
PRACTICE MAKES PERFECT

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.



```python
lines = []
while True:
    s = input()
    if s:
        lines.append(s.upper())
    else:
        break;

for sentence in lines:
    print(sentence)

```

    hello 
    jdfhjk
    skjdfgkj
    jdfhgbkj
    
    HELLO 
    JDFHJK
    SKJDFGKJ
    JDFHGBKJ
    

## Question 10
### Level 2

Question:
Write a program that accepts a sequence of whitespace separated words as input and prints the words after removing all duplicate words and sorting them alphanumerically.
Suppose the following input is supplied to the program:
hello world and practice makes perfect and hello world again
Then, the output should be:
again and hello makes perfect practice world

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.
We use set container to remove duplicated data automatically and then use sorted() to sort the data.


```python
input_str = input()
words = [word for word in input_str.split(" ")]
print(" ".join(sorted(list(set(words)))))
```

    hello world and practice makes perfect and hello world again
    again and hello makes perfect practice world
    

##  Question 11
### Level 2

Question:
Write a program which accepts a sequence of comma separated 4 digit binary numbers as its input and then check whether they are divisible by 5 or not. The numbers that are divisible by 5 are to be printed in a comma separated sequence.
Example:
0100,0011,1010,1001
Then the output should be:
1010
Notes: Assume the data is input by console.

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.



```python
value = []
items=[inputBinaryDig for inputBinaryDig in input().split(',')]
for p in items:
    DecNum = int(p, 2)
    if not DecNum%5:
        value.append(p)

print(','.join(value))

```

    0100,0011,1010,1001
    1010
    

## Question 12
### Level 2

Question:
Write a program, which will find all such numbers between 1000 and 3000 (both included) such that each digit of the number is an even number.
The numbers obtained should be printed in a comma-separated sequence on a single line.

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.



```python
values = []

def isNumb(number):
    flag = True
    while(number >=1 ):
        temp_var = number%10; #get unit place digit
        if temp_var % 2 != 0:
            flag = False
            break
        number = number//10; #remove the units place 
    return flag

    
for number in range(999, 3001):
    
    if isNumb(number):
        
        values.append(str(number))
        
print(",".join(values))

```

    2000,2002,2004,2006,2008,2020,2022,2024,2026,2028,2040,2042,2044,2046,2048,2060,2062,2064,2066,2068,2080,2082,2084,2086,2088,2200,2202,2204,2206,2208,2220,2222,2224,2226,2228,2240,2242,2244,2246,2248,2260,2262,2264,2266,2268,2280,2282,2284,2286,2288,2400,2402,2404,2406,2408,2420,2422,2424,2426,2428,2440,2442,2444,2446,2448,2460,2462,2464,2466,2468,2480,2482,2484,2486,2488,2600,2602,2604,2606,2608,2620,2622,2624,2626,2628,2640,2642,2644,2646,2648,2660,2662,2664,2666,2668,2680,2682,2684,2686,2688,2800,2802,2804,2806,2808,2820,2822,2824,2826,2828,2840,2842,2844,2846,2848,2860,2862,2864,2866,2868,2880,2882,2884,2886,2888
    

## Question 13
### Level 2

Question:
Write a program that accepts a sentence and calculate the number of letters and digits.
Suppose the following input is supplied to the program:
hello world! 123
Then, the output should be:
LETTERS 10
DIGITS 3

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.



```python
s = input()
Count = {"DIGITS":0, "LETTERS":0}
for Count in s:
    if s.isdigit():
        Count["DIGITS"] += 1
    elif s.isalpha():
        Count["LETTERS"] += 1
    else:
        pass
    
print("LETTERS", d["LETTERS"])
print("DIGITS", d["DIGITS"])
```

     hello world! 123
    LETTERS 10
    DIGITS 3
    

## Question 14
### Level 2

Question:
Write a program that accepts a sentence and calculate the number of upper case letters and lower case letters.
Suppose the following input is supplied to the program:
Hello world!
Then, the output should be:
UPPER CASE 1
LOWER CASE 9

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.


```python
s = input()
d={"UPPER CASE":0, "LOWER CASE":0}
for c in s:
    if c.isupper():
        d["UPPER CASE"]+=1
    elif c.islower():
        d["LOWER CASE"]+=1
    else:
        pass
print("UPPER CASE", d["UPPER CASE"])
print("LOWER CASE", d["LOWER CASE"])

```

    Hello world!
    UPPER CASE 1
    LOWER CASE 9
    

## Question 15
### Level 2

Question:
Write a program that computes the value of a+aa+aaa+aaaa with a given digit as the value of a.
Suppose the following input is supplied to the program:
9
Then, the output should be:
11106

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.


```python
a = input()
n1 = int( "%s" % a )
n2 = int( "%s%s" % (a,a) )
n3 = int( "%s%s%s" % (a,a,a) )
n4 = int( "%s%s%s%s" % (a,a,a,a) )
print(n1+n2+n3+n4)
```

    9
    11106
    

## Question 16
### Level 2

Question:
Use a list comprehension to square each odd number in a list. The list is input by a sequence of comma-separated numbers.
Suppose the following input is supplied to the program:
1,2,3,4,5,6,7,8,9
Then, the output should be:
1,3,5,7,9

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.



```python
values = input()
number = []
for x in values.split(","):
    if int(x)%2!=0:
        #print(number)
        number.append(x)            
print(",".join(number))
```

    1,2,3,4,5,6,7,8,9
    1,3,5,7,9
    

## Question 17
### Level 2

Question:
Write a program that computes the net amount of a bank account based a transaction log from console input. The transaction log format is shown as following:
D 100
W 200

D means deposit while W means withdrawal.
Suppose the following input is supplied to the program:
D 300
D 300
W 200
D 100
Then, the output should be:
500

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.


```python
netAmount = 0
while True:
    s = input()
    if not s:
        break
    values = s.split(" ")
    operation = values[0]
    amount = int(values[1])
    if operation=="D":
        netAmount+=amount
    elif operation=="W":
        netAmount-=amount
    else:
        pass
print(netAmount)
```

    D 300
    D 300
    W 200
    D 100
    
    500
    

## Question 18
### Level 3

Question:
A website requires the users to input username and password to register. Write a program to check the validity of password input by users.
Following are the criteria for checking the password:
1. At least 1 letter between [a-z]
2. At least 1 number between [0-9]
1. At least 1 letter between [A-Z]
3. At least 1 character from [$#@]
4. Minimum length of transaction password: 6
5. Maximum length of transaction password: 12
Your program should accept a sequence of comma separated passwords and will check them according to the above criteria. Passwords that match the criteria are to be printed, each separated by a comma.
Example
If the following passwords are given as input to the program:
ABd1234@1,a F1#,2w3E*,2We3345
Then, the output of the program should be:
ABd1234@1

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.



```python
import re
value = []
items=[x for x in input().split(',')]
for p in items:
    if len(p)<6 or len(p)>12:
        continue
    else:
        pass
    if not re.search("[a-z]",p):
        continue
    elif not re.search("[A-Z]",p):
        continue
    elif not re.search("[0-9]",p):
        continue
    elif not re.search("[$#@]",p):
        continue
    elif re.search("\s",p):
        continue
    else:
        pass
    value.append(p)
print(",".join(value))
```

    ABd1234@1,a F1#,2w3E*,2We3345
    ABd1234@1
    

## Question 19
### Level 3

Question:
You are required to write a program to sort the (name, age, height) tuples by ascending order where name is string, age and height are numbers. The tuples are input by console. The sort criteria is:
1: Sort based on name;
2: Then sort based on age;
3: Then sort by score.
The priority is that name > age > score.
If the following tuples are given as input to the program:
Tom,19,80
John,20,90
Jony,17,91
Jony,17,93
Json,21,85
Then, the output of the program should be:
[('John', '20', '90'), ('Jony', '17', '91'), ('Jony', '17', '93'), ('Json', '21', '85'), ('Tom', '19', '80')]

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.
We use itemgetter to enable multiple sort keys.


```python
from operator import itemgetter
l = []
while True:
    s = input()
    if not s:
        break
    l.append(tuple(s.split(",")))

print(sorted(l, key=itemgetter(0,1,2)))
```

    Tom,19,80
    John,20,90
    John,20,82
    Json,21,85
    Tom,19,82
    
    [('John', '20', '82'), ('John', '20', '90'), ('Json', '21', '85'), ('Tom', '19', '80'), ('Tom', '19', '82')]
    

## Question 20
### Level 3

Question:
Define a class with a generator which can iterate the numbers, which are divisible by 7, between a given range 0 and n.

Hints:
Consider use yield


```python
class findiv:

    def generator(n):
        list_of = range(1,n+1)
        for i in list_of:
            if i % 7 == 0:
                yield i

for i in generator(100):
    print (i)
```

    7
    14
    21
    28
    35
    42
    49
    56
    63
    70
    77
    84
    91
    98
    

## Question 21
### Level 3

Question
A robot moves in a plane starting from the original point (0,0). The robot can move toward UP, DOWN, LEFT and RIGHT with a given steps. The trace of robot movement is shown as the following:
UP 5
DOWN 3
LEFT 3
RIGHT 2
¡­
The numbers after the direction are steps. Please write a program to compute the distance from current position after a sequence of movement and original point. If the distance is a float, then just print the nearest integer.
Example:
If the following tuples are given as input to the program:
UP 5
DOWN 3
LEFT 3
RIGHT 2
Then, the output of the program should be:
2

Hints:
In case of input data being supplied to the question, it should be assumed to be a console input.


```python
import math
pos = [0,0]
while True:
    s = input()
    if not s:
        break
    movement = s.split(" ")
    direction = movement[0]
    steps = int(movement[1])
    if direction=="UP":
        pos[0]+=steps
    elif direction=="DOWN":
        pos[0]-=steps
    elif direction=="LEFT":
        pos[1]-=steps
    elif direction=="RIGHT":
        pos[1]+=steps
    else:
        pass

print(int(round(math.sqrt(pos[1]**2+pos[0]**2))))
```

    UP 5
    DOWN 3
    LEFT 3
    RIGHT 2 
    
    2
    

## Question 22
### Level 3

Question:
Write a program to compute the frequency of the words from the input. The output should output after sorting the key alphanumerically. 
Suppose the following input is supplied to the program:
New to Python or choosing between Python 2 and Python 3? Read Python 2 or Python 3.
Then, the output should be:
2:2
3.:1
3?:1
New:1
Python:5
Read:1
and:1
between:1
choosing:1
or:2
to:1

Hints
In case of input data being supplied to the question, it should be assumed to be a console input.


```python
freq = {}
line = input()
for word in line.split():
    freq[word] = freq.get(word,0)+1

words = freq.keys()
words.sort()

for w in words:
    print("%s:%d" % (w,freq[w]))
```

## Question 23
### level 1

Question:
Write a method which can calculate square value of number

Hints:
Using the ** operator



```python
def sqr(n):
    return n**2

print(sqr(2))
print(sqr(5))
```

    4
    25
    

## Question 24
### Level 1

Question:

Python has many built-in functions, and if you do not know how to use it, you can read document online or find some books. But Python has a built-in document function for every built-in functions.

Please write a program to print some Python built-in functions documents, such as abs(), int(), raw_input()

And add document for your own function
Hints:
The built-in document method is __doc__



```python
print(abs.__doc__)
print(int.__doc__)
print(input.__doc__)

def sqr(n):
    '''Return the square value of the input number.    
The input number must be integer.
    '''
    return n ** 2

print(sqr(5))
print(sqr.__doc__)
```

    Return the absolute value of the argument.
    int([x]) -> integer
    int(x, base=10) -> integer
    
    Convert a number or string to an integer, or return 0 if no arguments
    are given.  If x is a number, return x.__int__().  For floating point
    numbers, this truncates towards zero.
    
    If x is not a number or if base is given, then x must be a string,
    bytes, or bytearray instance representing an integer literal in the
    given base.  The literal can be preceded by '+' or '-' and be surrounded
    by whitespace.  The base defaults to 10.  Valid bases are 0 and 2-36.
    Base 0 means to interpret the base from the string as an integer literal.
    >>> int('0b100', base=0)
    4
    Forward raw_input to frontends
    
            Raises
            ------
            StdinNotImplentedError if active frontend doesn't support stdin.
            
    25
    Return the square value of the input number.    
    The input number must be integer.
        
    

## Question 25
### Level 1

Question:
Define a class, which have a class parameter and have a same instance parameter.

Hints:
Define a instance parameter, need add it in __init__ method
You can init a object with construct parameter or set the value later



```python
class student:
    Name =''
    Mid1_mark = 0
    Mid2_mark = 0
    Final_mark = 0
    
    def __init__(self,Name,Mid1_mark,Mid2_mark,Final_mark):
        self.Name = Name
        self.Mid1_mark = Mid1_mark
        self.Mid2_mark = Mid2_mark
        self.Final_mark = Final_mark
        
    def compute_tot_marks(self):
        total =  self.Mid1_mark +  self.Mid2_mark +  self.Final_mark
        print('Name: ', self.Name," Total Mark: ",total)
    
std1 = student('Dipu',20,20,55)
std1.compute_tot_marks()

std2 = student('Asad',19,18,53)
std2.compute_tot_marks()
```

    Name:  Dipu  Total Mark:  95
    Name:  Asad  Total Mark:  90
    

## Question 26:
Define a function which can compute the sum of two numbers.

Hints:
Define a function with two numbers as arguments. You can compute the sum in the function and return the value.


```python
def SumTwoNum(n1, n2):
    return n1+n2

print(SumTwoNum(5,5))
```

    10
    

## Question 27
Define a function that can convert a integer into a string and print it in console.

Hints:

Use str() to convert a number to string.


```python
def intTOstring(n):
    print(str(n))

intTOstring(93)
```

    93
    

## Question 28
Define a function that can convert a integer into a string and print it in console.

Hints:

Use str() to convert a number to string.


```python
def intTOstring(n):
    print(str(n))

intTOstring(93)
```

    93
    

## Question 29
Define a function that can receive two integral numbers in string form and compute their sum and then print it in console.

Hints:

Use int() to convert a string to integer.


```python
def addTwoStringInt(s1,s2):
    print(int(s1)+int(s2))

addTwoStringInt('90','3')
```

    93
    

## Question 30
Define a function that can accept two strings as input and concatenate them and then print it in console.

Hints:

Use + to concatenate the strings


```python
def ConcatTwoStr(s1,s2):
    print(s1+s2)

ConcatTwoStr('9','3')
```

    93
    

## Question 31
Define a function that can accept two strings as input and print the string with maximum length in console. If two strings have the same length, then the function should print al l strings line by line.

Hints:

Use len() function to get the length of a string


```python
def printStr(s1,s2):
    l1 = len(s1)
    l2 = len(s2)
    if l1>l2:
        print(s1)
    elif l2>l1:
        print(s2)
    else:
        print(s1, s2)
        
printStr('Nine',"Three")

```

    Three
    

## Question 32
Define a function that can accept an integer number as input and print the "It is an even number" if the number is even, otherwise print "It is an odd number".

Hints:

Use % operator to check if a number is even or odd.



```python
def oddOreven(n):
    if n%2 == 0:
        print("It is an even number")
    else:
        print("It is an odd number")
        
oddOreven(8)
```

    It is an even number
    

## Question 33
Define a function which can print a dictionary where the keys are numbers between 1 and 3 (both included) and the values are square of keys.

Hints:

Use dict[key]=value pattern to put entry into a dictionary.
Use ** operator to get power of a number.


```python
def printDict():
    d=dict()
    d[1]=1
    d[2]=22
    d[3]=33
    print(d)

printDict()
```

    {1: 1, 2: 22, 3: 33}
    

## Question 34
Define a function which can print a dictionary where the keys are numbers between 1 and 20 (both included) and the values are square of keys.

Hints:

Use dict[key]=value pattern to put entry into a dictionary.
Use ** operator to get power of a number.
Use range() for loops.



```python
def printDict():
    d=dict()
    for i in range(1,21):
        d[i]=i**2
    print(d)

printDict()
```

    {1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81, 10: 100, 11: 121, 12: 144, 13: 169, 14: 196, 15: 225, 16: 256, 17: 289, 18: 324, 19: 361, 20: 400}
    

## Question 35
Define a function which can generate a dictionary where the keys are numbers between 1 and 20 (both included) and the values are square of keys. The function should just print the values only.

Hints:

Use dict[key]=value pattern to put entry into a dictionary.
Use ** operator to get power of a number.
Use range() for loops.
Use keys() to iterate keys in the dictionary. Also we can use item() to get key/value pairs.


```python
def printDict():
    d=dict()
    for i in range(1,21):
        d[i]=i**2
    for (k,v) in d.items():	
        print(v)

printDict()
```

    1
    4
    9
    16
    25
    36
    49
    64
    81
    100
    121
    144
    169
    196
    225
    256
    289
    324
    361
    400
    

## Question 36
Define a function which can generate a dictionary where the keys are numbers between 1 and 20 (both included) and the values are square of keys. The function should just print the keys only.

Hints:

Use dict[key]=value pattern to put entry into a dictionary.
Use ** operator to get power of a number.
Use range() for loops.
Use keys() to iterate keys in the dictionary. Also we can use item() to get key/value pairs.


```python
def printDict():
    d=dict()
    for i in range(1,21):
        d[i]=i**2
    for (k,v) in d.items():	
        print(k)

printDict()
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    

## Question 37
Define a function which can generate and print a list where the values are square of numbers between 1 and 20 (both included).

Hints:

Use ** operator to get power of a number.
Use range() for loops.
Use list.append() to add values into a list.



```python
def printList():
    l=list()
    for i in range(1,21):
        l.append(i**2)
    print(l)

printList()
```

    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
    

## Question 38
Define a function which can generate a list where the values are square of numbers between 1 and 20 (both included). Then the function needs to print the first 5 elements in the list.

Hints:

Use ** operator to get power of a number.
Use range() for loops.
Use list.append() to add values into a list.
Use [n1:n2] to slice a list


```python
def printList():
    l=list()
    for i in range(1,21):
        l.append(i**2)
    print(l[:5])

printList()
```

    [1, 4, 9, 16, 25]
    

## Question 39
Define a function which can generate a list where the values are square of numbers between 1 and 20 (both included). Then the function needs to print the last 5 elements in the list.

Hints:

Use ** operator to get power of a number.
Use range() for loops.
Use list.append() to add values into a list.
Use [n1:n2] to slice a list


```python
def printList():
    l=list()
    for i in range(1,21):
        l.append(i**2)
    print(l[-5:])

printList()
```

    [256, 289, 324, 361, 400]
    

## Question 40
Define a function which can generate a list where the values are square of numbers between 1 and 20 (both included). Then the function needs to print all values except the first 5 elements in the list.

Hints:

Use ** operator to get power of a number.
Use range() for loops.
Use list.append() to add values into a list.
Use [n1:n2] to slice a list


```python
def printList():
    l=list()
    for i in range(1,21):
        l.append(i**2)
    print (l[5:])

printList()
```

    [36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
    

## Question 41
Define a function which can generate and print a tuple where the value are square of numbers between 1 and 20 (both included). 

Hints:

Use ** operator to get power of a number.
Use range() for loops.
Use list.append() to add values into a list.
Use tuple() to get a tuple from a list.


```python
def printTuple():
    l=list()
    for i in range(1,21):
        l.append(i**2)
    print(tuple(l))

printTuple()
```

    (1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400)
    

## Question 42
With a given tuple (1,2,3,4,5,6,7,8,9,10), write a program to print the first half values in one line and the last half values in one line. 

Hints:

Use [n1:n2] notation to get a slice from a tuple.



```python
tp=(1,2,3,4,5,6,7,8,9,10)

tp1=tp[:5]
tp2=tp[5:]

print(tp1, tp2)
```

    (1, 2, 3, 4, 5) (6, 7, 8, 9, 10)
    

## Question 43
Write a program to generate and print another tuple whose values are even numbers in the given tuple (1,2,3,4,5,6,7,8,9,10). 

Hints:

Use "for" to iterate the tuple
Use tuple() to generate a tuple from a list.


```python
tp=(1,2,3,4,5,6,7,8,9,10)
li=list()
for i in tp:
    if i%2==0:
        li.append(i)

tp2=tuple(li)
print(tp2)
```

    (2, 4, 6, 8, 10)
    

## Question 44
Write a program which accepts a string as input to print "Yes" if the string is "yes" or "YES" or "Yes", otherwise print "No". 

Hints:
Use if statement to judge condition.


```python
s= input()
if (s=='yes' or s=='YES' or s=='Yes'):
    print('Yes')
else:
    print('No')
```

    yes
    Yes
    

## Question 45
Write a program which can filter even numbers in a list by using filter function. The list is: [1,2,3,4,5,6,7,8,9,10].

Hints:

Use filter() to filter some elements in a list.
Use lambda to define anonymous functions.


```python
li = [1,2,3,4,5,6,7,8,9,10]
 
eve_num = filter(lambda x: x%2 == 0, li)
 
print(list(eve_num))
```

    [2, 4, 6, 8, 10]
    

## Question 46
Write a program which can map() to make a list whose elements are square of elements in [1,2,3,4,5,6,7,8,9,10].

Hints
Use map() to generate a list.
Use lambda to define anonymous functions.


```python
li = [1,2,3,4,5,6,7,8,9,10]
sqrNum = map(lambda x: x**2, li)
print(list(sqrNum))
```

    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
    

## Question 47
Write a program which can map() and filter() to make a list whose elements are square of even number in [1,2,3,4,5,6,7,8,9,10].

Hints
Use map() to generate a list.
Use filter() to filter elements of a list.
Use lambda to define anonymous functions.



```python
li = [1,2,3,4,5,6,7,8,9,10]
 
eve_num = map( lambda x: x**2, filter(lambda x: x%2 == 0, li))
 
print(list(eve_num))
```

    [4, 16, 36, 64, 100]
    

## Question 48
Write a program which can filter() to make a list whose elements are even number between 1 and 20 (both included).

Hints:

Use filter() to filter elements of a list.
Use lambda to define anonymous functions.


```python
eve_num = filter(lambda x: x%2 == 0, range(1,21))
 
print(list(eve_num))
```

    [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
    

## Question 49
Write a program which can map() to make a list whose elements are square of numbers between 1 and 20 (both included).

Hints
Use map() to generate a list.
Use lambda to define anonymous functions.



```python
sqrNum = map(lambda x: x**2, range(1,21))
print(list(sqrNum))
```

    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
    

## Question 50
Define a class named American which has a static method called printNationality.

Hints:
Use @staticmethod decorator to define class static method.



```python
class American(object):
    @staticmethod
    def printNationality():
        print("America")

obj1 = American()
obj1.printNationality()
American.printNationality()
```

    America
    America
    

## Question 51
Define a class named American and its subclass NewYorker. 

Hints:

Use class Subclass(ParentClass) to define a subclass.


```python
class American(object):
    pass

class NewYorker(American):
    pass

obj1 = American()
obj2 = NewYorker()
print(obj1)
print(obj2)
```

    <__main__.American object at 0x0000025DE30782E0>
    <__main__.NewYorker object at 0x0000025DE3035550>
    

## Question 52
Define a class named Circle which can be constructed by a radius. The Circle class has a method which can compute the area. 

Hints:

Use def methodName(self) to define a method.



```python
import math
class Circle(object):
    def __init__(self, r):
        self.radius = r

    def area(self):
        return self.radius**2*math.pi

aCircle = Circle(4)
print (round(aCircle.area(),2))
```

    50.27
    

## Question 53
Define a class named Rectangle which can be constructed by a length and width. The Rectangle class has a method which can compute the area. 

Hints:

Use def methodName(self) to define a method.


```python
class Rectangle(object):
    def __init__(self, l, w):
        self.length = l
        self.width  = w

    def area(self):
        return self.length*self.width

aRectangle = Rectangle(20,10.5)
print(round(aRectangle.area(),2))
```

    210.0
    

## Question 54
Define a class named Shape and its subclass Square. The Square class has an init function which takes a length as argument. Both classes have a area function which can print the area of the shape where Shape's area is 0 by default.

Hints:

To override a method in super class, we can define a method with the same name in the super class.


```python
class Shape(object):
    def __init__(self):
        pass

    def area(self):
        return 0

class Square(Shape):
    def __init__(self, l):
        Shape.__init__(self)
        self.length = l

    def area(self):
        return self.length**2

aSquare= Square(5)
print(round(aSquare.area(),2))
```

    25
    

## Question 55
Please raise a RuntimeError exception.

Hints:

Use raise() to raise an exception.



```python
raise RuntimeError('Error found in the 3rd loop')
```


    ---------------------------------------------------------------------------

    RuntimeError                              Traceback (most recent call last)

    <ipython-input-28-81d3efe54016> in <module>
    ----> 1 raise RuntimeError('Error found in the 3rd loop')
    

    RuntimeError: Error found in the 3rd loop


## Question 56
Write a function to compute 5/0 and use try/except to catch the exceptions.

Hints:

Use try/except to catch exceptions.


```python
def throws():
    return 5/0

try:
    throws()
except ZeroDivisionError:
    print("division by zero!")
except Exception, err:
    print('Caught an exception')
finally:
    print('In finally block for cleanup')
```


      File "<ipython-input-29-1211633063ea>", line 8
        except Exception, err:
                        ^
    SyntaxError: invalid syntax
    


## Question 57
Define a custom exception class which takes a string message as attribute.

Hints:

To define a custom exception, we need to define a class inherited from Exception.



```python
class MyError(Exception):
    """My own exception class

    Attributes:
        msg  -- explanation of the error
    """
    
    def __init__(self, msg):
        self.msg = msg

error = MyError("something wrong")
```

## Question 58
Assuming that we have some email addresses in the "username@companyname.com" format, please write program to print the user name of a given email address. Both user names and company names are composed of letters only.

Example:
If the following email address is given as input to the program:

john@google.com

Then, the output of the program should be:

john

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:

Use \w to match letters.


```python
import re
email = input()
pat2 = "(\w+)@((\w+\.)+(com))"
r2 = re.match(pat2,email)
print(r2.group(1))
```

    dipu@gmail.com
    dipu
    

## Question 59
Assuming that we have some email addresses in the "username@companyname.com" format, please write program to print the company name of a given email address. Both user names and company names are composed of letters only.

Example:
If the following email address is given as input to the program:

john@google.com

Then, the output of the program should be:

google

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:

Use \w to match letters.



```python
import re
email = input()
pat2 = "(\w+)@((\w+\.)+(com))"
r2 = re.match(pat2,email)
print(r2.group(2))
```

    dipu@gmail.com
    gmail.com
    

## Question 60
Write a program which accepts a sequence of words separated by whitespace as input to print the words composed of digits only.

Example:
If the following words is given as input to the program:

2 cats and 3 dogs.

Then, the output of the program should be:

['2', '3']

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:

Use re.findall() to find all substring using regex.



```python
import re
s = input()
print(re.findall("\d+",s))
```

    2 cats and 3 dogs
    ['2', '3']
    

## Question 61
Print a unicode string "hello world".

Hints:

Use u'strings' format to define unicode string.


```python
unicodeStr = u"hello world!"
print(unicodeStr)
```

    hello world!
    

## Question 62
Write a program to read an ASCII string and to convert it to a unicode string encoded by utf-8.

Hints:

Use unicode() function to convert.


```python
s = input()
u = s.encode('utf-8')
print(u)
```

    hello
    b'hello'
    

## Question 63

Write a special comment to indicate a Python source code file is in unicode.

Hints:



```python
#----------------------------------------#

# *-* ID:2019-1-60-093 *-*

#----------------------------------------#
```

## Question 64

Write a program to compute 1/2+2/3+3/4+...+n/n+1 with a given n input by console (n>0).

Example:
If the following n is given as input to the program:

5

Then, the output of the program should be:

3.55

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:
Use float() to convert an integer to a float


```python
sum=0.0
n=int(input())
for i in range(1,n+1):
    sum += float(float(i)/(i+1))
print(round(sum,2))
```

    5
    3.55
    

## Question 65

Write a program to compute:

f(n)=f(n-1)+100 when n>0
and f(0)=1

with a given n input by console (n>0).

Example:
If the following n is given as input to the program:

5

Then, the output of the program should be:

500

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:
We can define recursive function in Python.


```python
def f(n):
    if n == 0:
        return 0
    else:
        return f(n-1)+100

n=int(input())
print(f(n))
```

    5
    500
    

## Question 66
The Fibonacci Sequence is computed based on the following formula:

f(n)=0 if n=0
f(n)=1 if n=1
f(n)=f(n-1)+f(n-2) if n>1

Please write a program to compute the value of f(n) with a given n input by console.

Example:
If the following n is given as input to the program:

7

Then, the output of the program should be:

13

In case of input data being supplied to the question, it should be assumed to be a console input.

Hints:
We can define recursive function in Python.


```python
def f(n):
    if n == 0:
        return 0
    
    elif n == 1:
        return 1
    
    else:
        return f(n-1)+f(n-2)

n=int(input())
print(f(n))
```

    7
    13
    

## Question 67
The Fibonacci Sequence is computed based on the following formula:

f(n)=0 if n=0
f(n)=1 if n=1
f(n)=f(n-1)+f(n-2) if n>1

Please write a program using list comprehension to print the Fibonacci Sequence in comma separated form with a given n input by console.

Example:
If the following n is given as input to the program:

7

Then, the output of the program should be:

0,1,1,2,3,5,8,13


Hints:
We can define recursive function in Python.
Use list comprehension to generate a list from an existing list.
Use string.join() to join a list of strings.

In case of input data being supplied to the question, it should be assumed to be a console input.


```python
def f(n):
    if n == 0:
        return 0
    
    elif n == 1:
        return 1
    
    else:
        return f(n-1)+f(n-2)

n=int(input())

values = [str(f(x)) for x in range(0, n+1)]

print(",".join(values))
```

    7
    0,1,1,2,3,5,8,13
    

## Question 68

Please write a program using generator to print the even numbers between 0 and n in comma separated form while n is input by console.

Example:
If the following n is given as input to the program:

10

Then, the output of the program should be:

0,2,4,6,8,10

Hints:
Use yield to produce the next value in generator.

In case of input data being supplied to the question, it should be assumed to be a console input.



```python
def generateEven(n):
    i=0
    while i<=n:
        if i%2==0:
            yield i
        i+=1


n=int(input())
values = []
for i in generateEven(n):
    values.append(str(i))

print(",".join(values))
```

    10
    0,2,4,6,8,10
    

## Question 69
Please write a program using generator to print the numbers which can be divisible by 5 and 7 between 0 and n in comma separated form while n is input by console.

Example:
If the following n is given as input to the program:

100

Then, the output of the program should be:

0,35,70

Hints:
Use yield to produce the next value in generator.

In case of input data being supplied to the question, it should be assumed to be a console input.



```python
def NumGenerator(n):
    for i in range(n+1):
        if i%5==0 and i%7==0:
            yield i

n=int(input())
values = []
for i in NumGenerator(n):
    values.append(str(i))

print(",".join(values))
```

    100
    0,35,70
    

## Question 70
Please write assert statements to verify that every number in the list [2,4,6,8] is even.

Hints:
Use "assert expression" to make assertion.



```python
li = [2,4,6,8]
for i in li:
    assert i%2==0, 'Not all the items are even'
```

## Question 71
Please write a program which accepts basic mathematic expression from console and print the evaluation result.

Example:
If the following string is given as input to the program:

35+3

Then, the output of the program should be:

38

Hints:
Use eval() to evaluate an expression.




```python
expression = input()
print(eval(expression))
```

    1+2
    3
    

## Question 72
Please write a binary search function which searches an item in a sorted list. The function should return the index of element to be searched in the list.

Hints:
Use if/elif to deal with conditions.



```python
import math
def bin_search(li, element):
    bottom = 0
    top = len(li)-1
    index = -1
    while top>=bottom and index==-1:
        mid = int(math.floor((top+bottom)/2.0))
        if li[mid]==element:
            index = mid
        elif li[mid]>element:
            top = mid-1
        else:
            bottom = mid+1

    return index

li=[1,3,4,6,8,9,11,15,19,20]
print(bin_search(li,11))
print(bin_search(li,20))
```

    6
    9
    

## Question 73
Please write a binary search function which searches an item in a sorted list. The function should return the index of element to be searched in the list.

Hints:
Use if/elif to deal with conditions.



```python
import math
def bin_search(li, element):
    bottom = 0
    top = len(li)-1
    index = -1
    while top>=bottom and index==-1:
        mid = int(math.floor((top+bottom)/2.0))
        if li[mid]==element:
            index = mid
        elif li[mid]>element:
            top = mid-1
        else:
            bottom = mid+1

    return index

li=[1,3,4,6,8,9,11,15,19,20]
print(bin_search(li,11))
print(bin_search(li,19))
```

    6
    8
    

## Question 74
Please generate a random float where the value is between 10 and 100 using Python math module.

Hints:
Use random.random() to generate a random float in [0,1].



```python
import random
print(random.random()*100)
```

    13.424854878719572
    

## Question 75
Please generate a random float where the value is between 5 and 95 using Python math module.

Hints:
Use random.random() to generate a random float in [0,1].



```python
import random
print(round(random.random()*100-5,2))
```

    50.79
    

## Question 76
Please write a program to output a random even number between 0 and 10 inclusive using random module and list comprehension.

Hints:
Use random.choice() to a random element from a list.


```python
import random
print(random.choice([i for i in range(11) if i%2==0]))
```

    8
    

## Question 77
Please write a program to output a random number, which is divisible by 5 and 7, between 0 and 10 inclusive using random module and list comprehension.

Hints:
Use random.choice() to a random element from a list.


```python
import random
print(random.choice([i for i in range(201) if i%5==0 and i%7==0]))
```

    0
    

## Question 78
Please write a program to generate a list with 5 random numbers between 100 and 200 inclusive.

Hints:
Use random.sample() to generate a list of random values.



```python
import random
print(random.sample(range(100), 5))
```

    [44, 21, 60, 85, 55]
    

## Question 79
Please write a program to randomly generate a list with 5 even numbers between 100 and 200 inclusive.

Hints:
Use random.sample() to generate a list of random values.


```python
import random
print(random.sample([i for i in range(100,201) if i%2==0], 5))
```

    [150, 158, 198, 126, 162]
    

## Question 80
Please write a program to randomly generate a list with 5 numbers, which are divisible by 5 and 7 , between 1 and 1000 inclusive.

Hints:
Use random.sample() to generate a list of random values.



```python
import random
print(random.sample([i for i in range(1,1001) if i%5==0 and i%7==0], 5))
```

    [525, 455, 385, 420, 700]
    

## Question 81
Please write a program to randomly print a integer number between 7 and 15 inclusive.

Hints:
Use random.randrange() to a random integer in a given range.


```python
import random
print(random.randrange(7,16))
```

    14
    

## Question 82
Please write a program to compress and decompress the string "hello world!hello world!hello world!hello world!".

Hints:
Use zlib.compress() and zlib.decompress() to compress and decompress a string.


```python
import zlib
s = b'hello world!hello world!hello world!hello world!'
t = zlib.compress(s)
print(t)
print(zlib.decompress(t))
```

    b'x\x9c\xcbH\xcd\xc9\xc9W(\xcf/\xcaIQ\xcc \x82\r\x00\xbd[\x11\xf5'
    b'hello world!hello world!hello world!hello world!'
    

## Question 83
Please write a program to print the running time of execution of "1+1" for 100 times.

Hints:
Use timeit() function to measure the running time.


```python
from timeit import Timer
t = Timer("for i in range(100):1+1")
print(round(t.timeit(),2))
```

    1.51
    

## Question 84
Please write a program to shuffle and print the list [3,6,7,8].

Hints:
Use shuffle() function to shuffle a list.



```python
from random import shuffle
li = [3,6,7,8]
shuffle(li)
print(li)
```

    [8, 7, 6, 3]
    

## Question 85
Please write a program to shuffle and print the list [3,6,7,8].

Hints:
Use shuffle() function to shuffle a list.


```python
from random import shuffle
li = [3,6,7,8]
shuffle(li)
print(li)
```

    [7, 6, 8, 3]
    

## Question 86
Please write a program to generate all sentences where subject is in ["I", "You"] and verb is in ["Play", "Love"] and the object is in ["Hockey","Football"].

Hints:
Use list[index] notation to get a element from a list.


```python
subjects=["I", "You"]
verbs=["Play", "Love"]
objects=["Hockey","Football"]
for i in range(len(subjects)):
    for j in range(len(verbs)):
        for k in range(len(objects)):
            sentence = "%s %s %s." % (subjects[i], verbs[j], objects[k])
            print(sentence)
```

    I Play Hockey.
    I Play Football.
    I Love Hockey.
    I Love Football.
    You Play Hockey.
    You Play Football.
    You Love Hockey.
    You Love Football.
    

## Question 87
Please write a program to print the list after removing delete even numbers in [5,6,77,45,22,12,24].

Hints:
Use list comprehension to delete a bunch of element from a list.



```python
li = [5,6,77,45,22,12,24]
li = [x for x in li if x%2!=0]
print(li)
```

    [5, 77, 45]
    

## Question 88
By using list comprehension, please write a program to print the list after removing delete numbers which are divisible by 5 and 7 in [12,24,35,70,88,120,155].

Hints:
Use list comprehension to delete a bunch of element from a list.


```python
li = [12,24,35,70,88,120,155]
li = [x for x in li if x%5!=0 and x%7!=0]
print(li)
```

    [12, 24, 88]
    

## Question 89
By using list comprehension, please write a program to print the list after removing the 0th, 2nd, 4th,6th numbers in [12,24,35,70,88,120,155].

Hints:
Use list comprehension to delete a bunch of element from a list.
Use enumerate() to get (index, value) tuple.



```python
li = [12,24,35,70,88,120,155]
li = [x for (i,x) in enumerate(li) if i%2!=0]
print(li)
```

    [24, 70, 120]
    

## Question 90
By using list comprehension, please write a program generate a 3*5*8 3D array whose each element is 0.

Hints:
Use list comprehension to make an array.



```python
array = [[ [0 for col in range(8)] for col in range(5)] for row in range(3)]
print(array)
```

    [[[0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0]], [[0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0]], [[0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0, 0, 0]]]
    

## Question 91
By using list comprehension, please write a program to print the list after removing the 0th,4th,5th numbers in [12,24,35,70,88,120,155].

Hints:
Use list comprehension to delete a bunch of element from a list.
Use enumerate() to get (index, value) tuple.


```python
li = [12,24,35,70,88,120,155]
li = [x for (i,x) in enumerate(li) if i not in (0,4,5)]
print(li)
```

    [24, 35, 70, 155]
    

## Question 92
By using list comprehension, please write a program to print the list after removing the value 24 in [12,24,35,24,88,120,155].

Hints:
Use list's remove method to delete a value.


```python
li = [12,24,35,24,88,120,155]
li = [x for x in li if x!=24]
print(li)
```

    [12, 35, 88, 120, 155]
    

## Question 93
With two given lists [1,3,6,78,35,55] and [12,24,35,24,88,120,155], write a program to make a list whose elements are intersection of the above given lists.

Hints:
Use set() and "&=" to do set intersection operation.


```python
set1=set([1,3,6,78,35,55])
set2=set([12,24,35,24,88,120,155])
set1 &= set2
li=list(set1)
print(li)
```

    [35]
    

## Question 94
With a given list [12,24,35,24,88,120,155,88,120,155], write a program to print this list after removing all duplicate values with original order reserved.

Hints:
Use set() to store a number of values without duplicate.


```python
def removeDup( li ):
    newli=[]
    seen = set()
    for item in li:
        if item not in seen:
            seen.add( item )
            newli.append(item)

    return newli

li=[12,24,35,24,88,120,155,88,120,155]
print(removeDup(li))
```

    [12, 24, 35, 88, 120, 155]
    

## Question 95
Define a class Person and its two child classes: Male and Female. All classes have a method "getGender" which can print "Male" for Male class and "Female" for Female class.

Hints:
Use Subclass(Parentclass) to define a child class.


```python
class Person(object):
    def getGender( self ):
        return "Unknown"

class Male( Person ):
    def getGender( self ):
        return "Male"

class Female( Person ):
    def getGender( self ):
        return "Female"

aMale = Male()
aFemale= Female()
print(aMale.getGender())
print(aFemale.getGender())
```

    Male
    Female
    

## Question 96
Please write a program which count and print the numbers of each character in a string input by console.

Example:
If the following string is given as input to the program:

abcdefgabc

Then, the output of the program should be:

a,2
c,2
b,2
e,1
d,1
g,1
f,1

Hints:
Use dict to store key/value pairs.
Use dict.get() method to lookup a key with default value.



```python
dic = {}
s=input()
for s in s:
    dic[s] = dic.get(s,0)+1
print('\n'.join(['%s,%s' % (k, v) for k, v in dic.items()]))
```

    abcdefgabc
    a,2
    b,2
    c,2
    d,1
    e,1
    f,1
    g,1
    

## Question 97
Please write a program which accepts a string from console and print it in reverse order.

Example:
If the following string is given as input to the program:

rise to vote sir

Then, the output of the program should be:

ris etov ot esir

Hints:
Use list[::-1] to iterate a list in a reverse order.



```python
s=input()
s = s[::-1]
print(s)
```

    rise to vote sir
    ris etov ot esir
    

## Question 98
Please write a program which accepts a string from console and print the characters that have even indexes.

Example:
If the following string is given as input to the program:

H1e2l3l4o5w6o7r8l9d

Then, the output of the program should be:

Helloworld

Hints:
Use list[::2] to iterate a list by step 2.



```python
s=input()
s = s[::2]
print(s)
```

    H1e2l3l4o5w6o7r8l9d
    Helloworld
    

## Question 99
Please write a program which prints all permutations of [1,2,3]

Hints:
Use itertools.permutations() to get permutations of list.



```python
import itertools
print(list(itertools.permutations([1,2,3])))
```

    [(1, 2, 3), (1, 3, 2), (2, 1, 3), (2, 3, 1), (3, 1, 2), (3, 2, 1)]
    

## Question 100
Write a program to solve a classic ancient Chinese puzzle: 
We count 35 heads and 94 legs among the chickens and rabbits in a farm. How many rabbits and how many chickens do we have?

Hint:
Use for loop to iterate all possible solutions.


```python
def solve(numheads,numlegs):
    ns='No solutions!'
    for i in range(numheads+1):
        j=numheads-i
        if 2*i+4*j==numlegs:
            return i,j
    return ns,ns

numheads=35
numlegs=94
solutions=solve(numheads,numlegs)
print(solutions)
```

    (23, 12)
    
