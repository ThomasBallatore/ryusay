# Sets, Dicts, File I/O

## At start

* I'm going to take a bit of a different approach this section to mix things up. It will be a casual, chatty start through which I try to inspire introspective self-confidence to help students see how much they have learned so far...but in a way that leads into sets, dicts, and file I/O.
* I'll start the discussion by asking what type of things have they seen so far: not conditions or loops but objects including ints, floats, bool and None (showing print(type(x)))
* Then, I'll ask about other things that have an "inner life". strings, tuples, lists, sets, dicts and maybe range if nobody mentions it.
* That will lead to my example given below that I work out live, step-by-step.

---

## Taking attendance—showing lists, sets, dicts and how they relate

The idea is to figure out the most common letters in our collective names during section—a histogram without the figure. Each step is done live and in order of list, set then dict. Asking for student contributions the whole time.

```python
# Take attendance in a list! Use last names too if only a few people. 
names = ['henry', 'dimitri', 'ben', 'nabib', 'julia', 'sammota', 'simeon', 'devon', 'carolyn', 'thomas']

L = list() # show []
S = set()
D = dict() # show {}, talk about contrast with sets

for name in names:
    for letter in name:

        # List approach
        L.append(letter)

        # Unique letters in list without set
        # if letter not in L:
        #     L.append(letter)

        # Set approach Mention hashing, non-ordering
        S.add(letter) #show how append fails and why

        # Dictionary (stress key:value pairs)
        if letter in D:
            D[letter] += 1
        else:
            D[letter] = 1
        
        # Show pythonic one-liner
        D[letter] = D.get(letter, 0) + 1

# Just for fun, maybe I will demonstrate sort and lambda, perhaps after input/output in which they did sorting in Excel?        
for letter in sorted(D, key=lambda letter: D[letter], reverse=True):
    print(f"{letter}: {D[letter]}")
        
# print(D) # to show what dict looks like (or do in python tutor)
```

---

## File I/O

* I'll then demo how to write the output of line 48 above to a txt file basically with the following lines instead, and maybe not with sorted if I want to show how to sort in Excel to motivate the sorting discussion—I'll play that by ear.

```python
with open("output.txt", "w") as output:

    for letter in sorted(D, key=lambda letter: D[letter], reverse=True):
        output.write(f"{letter},{D[letter]}\n")
```

* I'll then demo how to read input from a txt file. Perhaps I'll write the names of the people in section into the file. I'll show the difference between .read(), .readline(), and .readlines()

```python
with open("pset4.txt", "r") as file:
    
    names = file.read() #demo readline() and readlines()
    print(names)
```

---

## Big breakout session

* Finally, I'll turn it over to students to work in an extended breakout session in which they find the most common letters in the pset 4 spec! A prepared file can be found here: https://gist.github.com/ThomasBallatore/ff3d5f4ee5de0b1e4b9b2d888915f511 Let's not worry about special characters, etc. The point is there are a lot of spaces, e's and a's and one & 😂

