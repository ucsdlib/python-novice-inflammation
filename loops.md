
* last lesson we wrote code to plot some values from our inflammation data.
![mean,max,min](fig/03-loop_2_0.png)
* but we have a dozen we want to do same for
* how to repeat things?


```python
#example task: print each character in a word
#one way to do is use a series of print statements
word = 'lead'
print(word[0])
print(word[1])
print(word[2])
print(word[3])
```

    l
    e
    a
    d


### This is a bad appoach b/c: 
1. doesnt scale - what if you wanted to print: supercalifragilisticexpialidocious - on for each 34 characters
2. fragile - long word it only prints partial; short sting it will throw error


```python
word = 'tin'
print(word[0])
print(word[1])
print(word[2])
print(word[3])
```

    t
    i
    n



    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-5-a51226538da7> in <module>()
          3 print(word[1])
          4 print(word[2])
    ----> 5 print(word[3])
    

    IndexError: string index out of range



```python
#better approach
word = 'lead'
for char in word:
    print (char)
    
```

    l
    e
    a
    d



```python
#better
word = 'supercalifragilisticexpialidocious'
for char in word:
    print (char)
    
```

    s
    u
    p
    e
    r
    c
    a
    l
    i
    f
    r
    a
    g
    i
    l
    i
    s
    t
    i
    c
    e
    x
    p
    i
    a
    l
    i
    d
    o
    c
    i
    o
    u
    s


* uses a `for loop` to repeat operations  
* general form: 

    ```python
    for variable in collection:
        do things with variable```
        
* loop variable can be arbitrary, need colon at the end
* indention necessary
* no command to end loop like many languages



```python
length = 0
for vowel in 'aeiou':
    length = length + 1
    #print(vowel, length)
print('There are', length, 'vowels')
```

    There are 5 vowels


Let's trace the execution:
1. length is 1, vowel is 'a'
2. length is 2, vowel is 'e'
3. length is 3, vowel is 'i'
4. length is 4, vowel is 'o'
5. length is 5, vowel is 'u'




```python
#note loop var still exists after loop
letter = 'z'
for letter in 'abc':
    print(letter)
print('after the loop, letter is', letter)
```

    a
    b
    c
    after the loop, letter is c


* finding the length of a string is such a common operation that Python actually has a built-in function to do it called len:



```python
print(len('aeiou'))

```

    5


* for loop is a way to do operations many times, a list is a way to store many values
* lists are builtins
* use []

## Loop challenge: 

Python has a built-in function called range that creates a sequence of numbers. Range can accept 1-3 parameters. If one parameter is input, range creates an array of that length, starting at zero and incrementing by 1. If 2 parameters are input, range starts at the first and ends at the second, incrementing by one. If range is passed 3 parameters, it starts at the first one, ends at the second one, and increments by the third one. For example, range(3) produces the numbers 0, 1, 2, while range(2, 5) produces 2, 3, 4, and range(3, 10, 3) produces 3, 6, 9. Using range, write a loop that uses range to print the first 3 natural numbers:

1  
2  
3  


```python
# solution
for i in range(1, 4):
   print(i)
```

    1
    2
    3


## Loop challenge 2:

Exponentiation is built into Python:

```python
print(5 ** 3)
125
```

Write a loop that calculates the same result as 5 ** 3 using multiplication (and without exponentiation).


```python
result = 1
for i in range(0, 3):
   result = result * 5
print(result)
```

    125


## Loop challenge 3:

Write a loop that takes a string, and produces a new string with the characters in reverse order, so 'Newton' becomes 'notweN'.


```python
newstring = ''
oldstring = 'Newton'
length_old = len(oldstring)
for char_index in range(length_old):
   newstring = newstring + oldstring[length_old - char_index - 1]
print(newstring)

```

    notweN



```python
reverse('newton')
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-4-4729264701a3> in <module>()
    ----> 1 reverse('newton')
    

    NameError: name 'reverse' is not defined



```python

```
