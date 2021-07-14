# ryusay
Ryusay Website

# Modules, strings, loops, random

## At start

* Begin with reminder about ensuring Proctorio works *before* the test. Perhaps highlighting https://canvas.harvard.edu/courses/87783/external_tools/75496
* Pep talk about how far they have come, hang in there, etc.
* Ask what questions do they have about anything, material, logistics, etc. to this point.


## Warm up: Easy strings with review of returns

(Breakout rooms)
#1. Write a function that prints out each character of a given string, each on its own line.

```python
def chars(s):
    for c in s:
        print(c)
    # Alternative
    # for i in range(len(s)):
        # print s[i]
```

In main session, perhaps challenge them to change the default end="\n" of print such that the characters appear on the same line?

(Main room because it is so short)
#2. Write a function that returns true if the number of characters in a given string is odd, and false if it is even.

```python
def odd(s):
    return len(s) % 2 == 1
    # return len(s) % 2 != 0
```

(Breakout rooms)
#3. Write a function that returns the fourth letter of a given string, or None if the string has fewer than 4 letters.

```python
def fourth(s):
    if len(s) < 4:
        return None
    else:
        return s[3]

# If an advanced group, perhaps show the "ternary" operator in Python just to expose them to it.
# def fourth(s):
#     return s[3] if len(s) < 4 else None
```

## More complex string operations

Briefly show in your IDE or Python Tutor how you can compare strings, perhaps with “a” < “b”, “b”>”a”, “aaa” == “aaa” or whatever. You might mention that underneath the hood, these are just ASCII values so there really is just math happening here. Note that "a" < "A" returns False. Note false vs. False as there were many errors on the last pset about this. If an advanced group, show print(ord("a"))?

Also, remind them about string slicing. Perhaps quickly in the terminal showing s = "Henry", s[1] is "e" and so on.

(Breakout rooms but warn this one is not so easy—feel free to end early and demo)
4. Write a function that returns true or false based on whether a given string is in alphabetical order. Here aaa is in alphabetical order.

```python
def order(s):
    for i in range(len(s) - 1): # try first without -1, and for s = "abcax". Then show error with "abcd".
        if s[i] > s[i+1]:
            return False
    return True

order("abcd")
order("axed")
```

Next, briefly show problem 5 statement below and note that this https://docs.python.org/3/library/string.html#string-constants exists. Remind them with demo how to import a module, perhaps using these two examples to illustrate different ways:

```python
# one way
from string import ascii_letters
print(ascii_letters)

# another way
import string
print(string.ascii_letters)
```

(Breakout rooms)
5. Write a function that returns True if all characters in the given string are in [a-z,A-Z]. Otherwise, return False

```python
from string import ascii_letters
print(ascii_letters)

def only_alpha(s):
    for letter in s:
        if letter not in ascii_letters:
            return False
    return True

only_alpha("xYZ")
only_alpha("xY2") # see what I did there 😂
```

It's possible to talk about casting ascii_letters as a list or better yet, as a set, but probably no time and perhaps a bit early. Still, with an advanced group, it might make sense?

## While loops

(Main room: take inputs and do it collectively. This tees up the harder question 7 below for breakout rooms.)
6. Convert the following for loop to a while loop:
	for i in range(10):
		print(i)

```python
counter = 0
while counter < 10:
    print(counter)
    counter += 1 # Make sure they know this is counter = counter + 1 and read = as "gets" not "equals" to be instructively pedantic.
```

(Breakout rooms)
7. Convert the following for loop to a while loop:
	for i in range(30, 6, -3):
		print(i)

```python
counter = 30
while counter > 6:
    print(counter)
    counter -= 3
```

## random

8. Write a program that randomly generates numbers in the range [1,12] and prints them, until it generates a 7, at which point it prints "Winner!".

```python
import random

def lucky_seven():
    n = 0
    while (n != 7):
        n = random.randint(1,12)
        print(n)
    print(n)

lucky_seven()
```

Show how in the IDE, the numbers are psuedo random (or appear to be), but in Python Tutor the same result happens every time!

If time allows, have them add a counter to see how many times it takes, on average, to get a 7.

Perhaps mention how randint is just an alias for randrange(a, b+1)
https://docs.python.org/3/library/random.html#random.randint

Make sure people feel comfy looking up documentation!
