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

*(Breakout rooms)* <br>
**#5. Write a method that takes a 2_d list and returns the lengths of its rows. See code below.** <br>
Feels like a good problem to wrap up with. I doubt anyone will show the list comp solution but that is a nice "bonus" at the end.

```python
def main():
    jagged = [
        [1, 2, 3],
        [4, 5],
        [6],
    ]
    lengths = row_lengths(jagged)
    print("row lengths: ", lengths)
  
def row_lengths(a):
    # PROBLEM: Write a method that takes a 2_d list and returns the lengths of its rows.

main()
```
ANSWER:
```python
def main():
    jagged = [
        [1, 2, 3],
        [4, 5],
        [6],
    ]
    lengths = row_lengths(jagged)
    print("row lengths: ", lengths)
  
def row_lengths(a):
    # PROBLEM: Write a method that takes a 2_d list and returns the lengths of its rows.

main()
```python
def main():
    jagged = [
        [1, 2, 3],
        [4, 5],
        [6],
    ]
    lengths = row_lengths(jagged)
    print("row lengths: ", lengths)
    
def row_lengths(a):
    # create list to hold length values
    lengths = []
    # iterate over elements of a, i.e. jagged
    for row in a:
    # append row to lengths
        lengths.append(row)
    # return list of lengths
    return lengths
    
    # demo this nice list comp if it feels appropriate
    return [len(row) for row in a]

main()
```
