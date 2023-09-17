# Day 1

## methods
```python
# print(), \n, \", input()
print("Hello, world!\nGoodbye, \"world\"")
input("What is your name?")

# input() will get user input in console 
# Then print() will print the word "Hello" and the user input
print("Hello " + input("What is your name? "))

# len()
print(len(input("What is your name? ")))
```

## variables
```python
name = input("What is your name? ")
length = len(name)

# snake case
user_name = input("What is your name? ")

# privileged words (keywords)
input = input("What is your name? ") # invalid

# numbers in names
1_player_username = "jackbauer" # invalid
player1_username = "jackbauer" # valid
```

---
# Day 2

## data types
```python
# data types
# string
# subscript
print("Hello"[0]) # => H

print(123 + 345) # => 468

# large integers
123_456_789

# float
3.14159

# boolean
True
False

# type errors
print("Hello, " + 123) # => TypeError: can only concatenate str (not "int") to str

# type checking - type()
num_char = len(input("What is your name? "))
print(type(num_char)) # => <class 'int'>

# type conversion/casting - str() 
new_num_char = str(num_char)
print("Your name has " + new_num_char + " characters.")

a = float(123)
print(type(a)) # => <class 'float'>

print(70 + float("100.5")) # => 170.5
print(str(70) + str(100)) # => 70100

two_digit_number = input("Type a two digit number: ") # => 35
print(int(two_digit_number[0]) + int(two_digit_number[1])) # => 8

print(type(input())) # => <class 'str'>
```

## mathematical operations
```python
3 + 5
7 - 4
3 * 2
6 / 3
print(2 ** 3) # => 8

# PEMDASLR
# ()
# **
# * /
# + -

print(3 * 3 + 3 / 3 - 3) # => 7.0
print(3 * (3 + 3) / 3 - 3) # => 3.0
```

---
# Day 3 

## control flow with if / else and conditional operators
```python
if condition: 
	do this
else:
	do this

water_level = 50 
if water_level > 80:
	print("Drain water")
else:
	print("Continue")

# comparison operators
>
<
>=
<=
==
!=

# nested if statements and elif statements
if condition:
	if another condition: 
		do this
	else: 
		do this
else:
	do this

# if / elif / else
if condition1:
	do A
elif condition2:
	do B
else: 
	do this

# leap year
is_leap = year % 400 == 0 if year % 100 == 0 else year % 4 == 0

# multiple if statements in succession 
if condition1:
	do A
if condition2:
	do B
if condition3:
	do C

# logical operators
if condition1 & condition2 & condition3
	do this
else: 
	do this

# and, not, or
a = 12
not a > 15 # => True
```

---
# Day 4

## randomness
```python
# module
import random 

random_integer = random.randint(1, 10)

print(my_module.pi)

random_float = random.random()

result = random.randint(0, 1)
```

## lists
```python
states_of_america = ["Detroit", "Ohio", "Pennsylvania"]
states_of_america[-1] = "Pencilvania"

states_of_america.append("Angelaland")

states_of_america.extend(["Angelaland", "Jack Bauer Land"])

# banker roulette
names_string = input("Give me everybody's names, separated by a comma. ")
names = names_string.split(", ")

no_of_people = len(names)
rand_index = random.randint(0, no_of_people - 1)

print(f"{names[rand_index]} is going to buy the meal today!")

# or
person_who_will_pay = random.choice(names)

num_of_states = len(states_of_america)
print(states_of_america[num_of_states - 1])

fruits = [...]
vegetables = [...]
dirty_dozen = [fruits, vegetables]
print(dirty_dozen) # => [[...], [...]]
```

---
# Day 5

## loops
```python
for item in list_of_items:
	# Do something to each item

# average height
student_heights = input("Input a list of student heights").split()
for n in range(0, len(student_heights)):
	student_heights[n] = int(student_heights[n])

# without sum() or len()
total = 0
num = 0
for height in student_heights: 
	total += height
	num += 1
print(round(total / num))

# with
print(round(sum(student_heights) / len(student_heights)))

# max() and min()
print(max(student_scores)) # => the highest value in a particular list
print(min(student_scores)) # => the lowest value

# without
highest = 0
for score in student_scores:
	if score > highest: 
		highest = score
print(highest)
```

## range
```python
# for loop with range
for number in range(1, 11, 3):
	print(number)

total = 0
for number in range(1, 101):
	total += number
print(total)
```

## project 5 - password generator
```python
for i in range(0, nr_letters): 
  password += random.choice(letters)
for i in range(0, nr_symbols): 
  password += random.choice(symbols)
for i in range(0, nr_numbers):
  password += random.choice(numbers)

l = list(password)
random.shuffle(l)
shuffled = ''.join(l)
print(shuffled)
```

---
# Day 6

## functions
```python
def my_function():
	print("Hello")
	print("Bye")

my_function()
```

## while
```python
while something_is_true:
	# do something repeatedly

while not at_goal():
	jump()

while not at_goal():
	if front_is_clear():
		move()
	else:
		jump()

def jump():
    turn_left()
    while wall_on_right():
        move()
    turn_right()
    move()
    turn_right()
    while front_is_clear():
        move()
    turn_left()
```

## project 6 - maze
```python
while not at_goal():
    if right_is_clear():
        turn_right()
    if front_is_clear():
        move()
    else:
        turn_left()
```

---
# Day 7

```python
# loop with index
for i in range(len(chosen_word)):
	if guess == chosen_word[i]:
		display[i] = guess

# join a list into a string
''.join(display)

# import all from module
from hangman import *
```

---
# Day 8

```python
# function with parameter
def greet_with(name, location):
	print(f"Hello, {name}")
	print(f"What is it like in {location}")

# positional argument
greet_with("Angela", "nowhere")

# parameter: name of the data that's being passed in
# argument: the value of the data

# keyword arguments
def my_function(a, b, c):
	# ...

my_function(c=3, a=1, b=2)

if new_position > 25: 
	new_position %= 26
```

---
# Day 9

## dictionaries & nesting
```python
dictionary == object

programming_dictionary = {
	"Bug": "An error in a program that prevents the program from running as expected.",
	"Function": "A piece of code that you can easily call over and over again.",
}

# Retrieving items from dictionary.
print(programming_dictionary["Bug"])

# Adding new items to dictionary.
programming_dictionary["Loop"] = "The action of doing something over and over again."

# Create an empty dictionary.
empty_dictionary = {}

# Wipe an existing dictionary 
# programming_dictionary = {}

# Edit an item in a dictionary
programming_dictionary["Bug"] = "A moth in your computer."

# Loop through a dictionary
for key in programming_dictionary:
	print(key)
	print(programming_dictionary[key])

# Nesting
{
 Key: [List],
 Key2: {Dict},
}

# Nesting a List in a Dictionary 
travel_log = {
	"France": ["Paris", "Lille", "Dijon"],
	"Germany": ["Berlin", "Hamburg", "Stuttgart"],
}

# Nesting Dictionary in a Dictionary
travel_log = {
	"France": {
		"cities_visited": ["Paris", "Lille", "Dijon"],
		"total_visits": 12
	},
	"Germany": {
		"cities_visited": ["Berlin", "Hamburg", "Stuttgart"],
		"total_visits": 5,
	}
}

[
	{
		Key: [List],
		Key2: {Dict},
	},
	{
	 Key: Value,
	 Key2: Value,
	},
]

# Nesting Dictionary in a List
travel_log = [
	{
		"country": "France",
		"cities_visited": ["Paris", "Lille", "Dijon"],
		"total_visits": 12
	},
	{
		"country": "Germany",
		"cities_visited": ["Berlin", "Hamburg", "Stuttgart"],
		"total_visits": 5,
	}
]

def add_new_country(country, visits, cities):
	new_country = {
		"country": country,
		"visits": visits,
		"cities": cities,
	}
	
	travel_log.append(new_country)
```

---
# Day 10

## functions with outputs
```python
def my_function():
	return 3 * 2

def format_name(f_name, l_name):
	if not f_name or not l_name:
		return # "You didn't provide valid inputs."
	return f"Result: {f_name} {l_name}".title()

print(format_name(input("What is your first name? "), input("What is your last name? ")))
```

```python
def is_leap(year):
	return year % 400 == 0 if year % 100 == 0 else year % 4 == 0

def days_in_month(year, month):
	"""Take a year and month and return the days in that month"""
	month_days = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
	if month == 2 and is_leap(year):
		return 29
	else:
		return month_days[month - 1]
```

```python
def add(n1, n2):
	return n1 + n2

operations = {
	'+': add,
}
```

---
# Day 11
## blackjack
```python
for thing in array: 
```

---
# Day 12
## global scope
- avoid modifying global scope

```python
enemies = 1
def increase_enemies():
	global enemies
	enemies += 1
```

```python
def increase_enemies():
	return enemies + 1
enemies = increase_enemies()
```

```python
GLOBAL_VARIABLE = 1
```

---
# Day 13
## bugs

---
# Day 14
## higher or lower

---
# Day 15
## installing python locally on your computer

---
# Day 16
## oop 

---
# Day 17
## making classes

---
# Day 18
## hirstle painting