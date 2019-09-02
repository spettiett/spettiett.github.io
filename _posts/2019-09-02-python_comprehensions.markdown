---
layout: post
title:      "Python Comprehensions"
date:       2019-09-02 19:48:40 +0000
permalink:  python_comprehensions
---


```
Several types of comprehensions are supported in both Python 2 and Python 3:

•	List comprehensions
•	Dictionary comprehensions
•	Set comprehensions
•	Generator comprehensions

Python List Comprehensions
List comprehensions provide a short and concise way to create lists. It consists of square brackets containing an expression followed by a for clause, then zero or more for or if clauses. The expressions can be anything, meaning you can put in all kinds of objects in lists. The result would be a new list made after the evaluation of the expression in context of the if and for clauses.

Syntax: 

variable = [out_exp for out_exp in input_list if out_exp == 2]

out_exp, an output expression
input_list, represents the input dataset/list

Python List Comprehension basically a one line for loop that produces a Python list data structure.
Example:
For Loop
	for i in range(5):
      		print(i)

RESULT: [0, 1, 2, 3, 4]

List Comprehension
x = [i for i in range(5)]
print(x)

RESULT: [0, 1, 2, 3, 4]


Common use cases for List Comprehensions
1)	To apply a function on to every element in a list, such as when you need to cast a bunch of strings into integers:

x = ['1', '2', '3', '4', '5']
y = [int(i) for i in x]
y

RESULT: [1, 2, 3, 4, 5]

2)	To loop over a list of strings and call a string method, such as strip on them because they had all kinds of leading or ending white space:

myStrings = [s.strip() for s in myStringList]

3)	To test an expression and apply a mathematical operation: 

multiples = [i for i in range(30) if i % 3 == 0]
print(multiples)

RESULT: [0, 3, 6, 9, 12, 15, 18, 21, 24, 27]

4)	To test an expression and apply a mathematical operation:

n_prod_2 = [2 * n for n in (0, 1, 2) if n > 0]
n_prod_2 

RESULT: [2, 4]

This can be read as: n_prod_2 is the list of all numbers 2 times n where n is an item in the (0, 1, 2) tuple, for which tuple element is greater than zero.

5)	To make a new list by appending to it in each iteration of the for loop:

Example:
For Loop
	square_num = []
for num in range(10):
    	square_num.append(num **2)
print(square_num)

RESULT: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

List Comprehension
square_num = [ num**2 for num in range(10)]
print(square_num)

RESULT: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
Python Dictionary Comprehensions
Dictionary Comprehensions are pretty similar to a list comprehension in the way that they are organized.  The only difference is that they use braces {}:

print( {i: str(i) for i in range(5)} )

RESULT: {0: '0', 1: '1', 2: '2', 3: '3', 4: '4'}

This Dictionary Comprehension is basically, creating an integer key and string value for each item in the range. 



Common use cases for Dictionary Comprehensions
1)	To swap the dictionary’s keys and values. 

my_dict = {1:"dog", 2:"cat", 3:"hamster"}
print( {value:key for key, value in my_dict.items()} )

RESULT: {'hamster': 3, 'dog': 1, 'cat': 2}
 
Python Set Comprehensions
Set comprehensions are created in much the same way as dictionary comprehensions, uses braces {}:

Example:

squared = {x**2 for x in [1, 1, 2]}
print(squared)

RESULT:  {1, 4}

Note: Python set is much like a mathematical set in that it doesn’t have any repeated elements.  As you can see from the example above, the call to set has removed the duplicates from the list.

Example:
my_list = [1, 2, 2, 3, 4, 5, 5, 7, 8]
my_set = {x for x in my_list}
my_set

RESULT:  {1, 2, 3, 4, 5, 7, 8}

Python Generator Comprehensions
They are also similar to list comprehensions. The only difference is that they don’t allocate memory for the whole list but generate one item at a time, thus more memory efficient.

Example:

multiples_gen = (i for i in range(10) if i % 3 == 0)
print(multiples_gen)
	     RESULT: <generator object <genexpr> at 0x000002829AE295E8>


for x in multiples_gen:
print(x)

RESULT: 
<generator object <genexpr> at 0x000002829AE295E8>
0
3
6
9

```
