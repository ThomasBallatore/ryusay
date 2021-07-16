# Chars and lists

## At start

* Start with small talk about test. Praise students for jumping right back in to lecture and homework.

---

## Characters are really just numbers

Just to kick the discussion off, I'll ask people what they thought about the idea that characters are just numbers. Last section, I had actually introduced the asciibetical idea for comparing chars/strings and will just casually review it here. I'll show an ASCII table and ask if they notice that upper and lower case are 32 apart. I'll show .tolower() in some simple program. Then I'll ask how they think that works, i.e. iterating along string, changing as appropriate, etc. Maybe I'll show in decimal how it is +32, and maybe I'll show how in binary (just to remind them about binary) that going from 65 to 97 is just a simple bit flip.

## Lists

*(Breakout rooms)* <br>
**#0. Write a function that takes in a list of temperatures and prints the average and how many exceeded that average. Assume the list is non-emtpy** <br>
I like this problem as a gentle use of lists but with a good review of previous work. It feels like a good challenge to start the section with and I hope most can succeed.

```python
def average_temp(temps):
    '''Prints the average temp and number of days exceeding'''
    ???

def main():
    temps = [60, 62, 85, 90, 70, 72, 84]
    print('Temps this week:', temps)
    average_temp(temps)

main()
```
ANSWER:
```python
def average_temp(temps):
    '''Prints the average temp and number of days exceeding'''
    average = 0
    for t in temps:
        average += t
    average = average/len(temps)
    print(f'The average temp was {average:.1f}.')
    
    num_over = 0
    for t in temps:
        if t > average:
            num_over += 1
    print(f'And {num_over} exceeded the average.')

def main():
    temps = [60, 62, 85, 90, 70, 72, 84]
    print('Temps this week:', temps)
    average_temp(temps)

main()
```

---

*(Breakout rooms)* <br>
**#1. Write a function that takes a list and prints out every other item of the list.**

```python
def every_other(l):
    for i in range(0, len(l), 2):
        print(l[i])

# every_other([2,3,4,5])
```

---

*(Main room, just asking for hands)* <br>
**#1b. Change the function so it prints every other item starting from the back.**

```python
def other_every(l):
    for i in range(len(l) - 1, -1, -2):
        print(l[i])

# other_every([2,3,4])
```

---

*(Breakout rooms)* <br>
**#2. Write a function that takes an integer N, and creates and returns a list of N random integers between 1 and 10, inclusive.**

```python
import random
def rand_list(n):
    ret = []
    for i in range(n):
        ret.append(random.randint(1,10))
    return ret

print(rand_list(4))
```

---

*(Breakout rooms but warn this one is not so easy—feel free to end early and demo)* <br>
**3. Write a function that takes a list, and returns True if all the numbers are the same.**

```python
def all_same(l):
    for item in l:
        if item != l[0]:
            return False
    return True

print(all_same([2,2,4]))
print(all_same([2,2,2]))
```

---


*(Breakout rooms)* <br>
**4. Write a function that takes a list and a number N, and returns True if two adjacent 
numbers in the list sum to N.**<br>
Note: I skipped the original 4 in the old repo. Seems a bit harder than this one. Don't expect to have time for that one.

```python
def adjacent(l,n):
    for i in range(len(l)-1):
        if l[i] + l[i+1] == n:
            return True
    return False

print(adjacent([2,5,2], 7))
print(adjacent([2,5,2], 4))
```

---

## While loops

*(Main room: take inputs from students and do it collectively. This tees up the harder question 7 below for breakout rooms.)* <br>
**6. Convert the following for loop to a while loop:**
```python
for i in range(10):
    print(i)
```
Answer
```python
counter = 0
while counter < 10:
    print(counter)
    counter += 1 # Make sure they know this is counter = counter + 1 and read = as "gets" not "equals" to be instructively pedantic.
```

---

*(Breakout rooms)* <br>
**7. Convert the following for loop to a while loop:**
```python
for i in range(30, 6, -3):
    print(i)
```
Answer
```python
counter = 30
while counter > 6:
    print(counter)
    counter -= 3
```

---

## Random module

*(Breakout rooms, if time allows)* <br>
**8. Write a program that randomly generates numbers in the range [1,12] and prints them, until it generates a 7, at which point it prints "Winner!".**

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

*Notes: Show how in the IDE, the numbers are psuedo random (or appear to be), but in Python Tutor the same result happens every time!*

*If time allows, have them add a counter to see how many times it takes, on average, to get a 7.*

*Perhaps mention how randint is just an alias for randrange(a, b+1)
https://docs.python.org/3/library/random.html#random.randint*

*Make sure people feel comfy looking up documentation!*
