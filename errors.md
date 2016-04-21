
## Errors and Exceptions

* every programmer deals with errors and they can be v. frustrating 
* understanding what the different error types are and when you are likely to encounter them helps a lot
* Errors in python ahve a specific form, called a **traceback**, let's look


```python
cd code
```

    /Users/jtdennis/workshops/python-novice-inflammation/code



```python
import errors_01
```


```python
errors_01.favorite_ice_cream()
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-10-44b1b870e6a6> in <module>()
    ----> 1 errors_01.favorite_ice_cream()
    

    /Users/jtdennis/workshops/python-novice-inflammation/code/errors_01.py in favorite_ice_cream()
          5         "strawberry"
          6     ]
    ----> 7     print(ice_creams[3])
    

    IndexError: list index out of range


* Two levels in this traceback:
    - the first shows code from teh cell above with an arrow pointing to line 2 (favorite_ice_cream()).
    - the second shows somce code in the other function (favorit_ice_cream, located in the file error_01.py on line 7. 
    - This is where the actual error happened. 

**LONG tracebacks**

* sometimes tracebacks are very long (20 levels deep)
* this can make it seem like something terrible has happened, but just means your program called many functions before the error
* Most times you can just go to the bottom on the trace

* What error did we get above? 
* Last line tells us the type - IndexError and a message "list index out of range"

* if you encoutner an error and don't know what it means, read the trace closely
* that way if you fix the and then encounter a new one, you can tell that the error change
* sometimes just knowing where the error occured is enough to fix it

** Don't the error**
* look at the official documentation on errors on docs.python.org (google it)
* it might not be there - it might be a custom error

**Syntax Errors**

* when you forget a colon at the end of a line, add one space too man when indenting uder an if statement, forget parenthesis -- you'll get a syntax errror
* this means python  couldn't figure out how to read your program
* this is similar to forgetting punctuation in English: 

>this text is difficult to read there is no punctuation there is also no capitalization why is this hard because you have to figure out where each sentence ends you also have to figure out where each sentence begins to some extent it might be ambiguous if there should be a sentence break or not


* if python can't figure out how to read a program, it will give up and inform you


```python
def some_function()
    msg = "hello, world"
    print(msg)
      return msg
```


      File "<ipython-input-12-3db28f89eee6>", line 1
        def some_function()
                           ^
    SyntaxError: invalid syntax



* python tells us that there's a syntax error on line 1
* event puts a little error where the issue is
* we missed the colon at the end of the function definition
* let's fix it


```python
def some_function():
    msg = "hello, world"
    print(msg)
      return msg
```


      File "<ipython-input-13-65a4c5904cb1>", line 4
        return msg
        ^
    IndentationError: unexpected indent



* ah, we actually had two errors in that code
* now we see an 'IndentationError' and the arrow pointing to the 'return' statement
* this tells us or indentation is off on that line

* **SyntaxError** and **IndentationError** indicate a problem with syntax in your program
* **IndentationError** is more specific - it always means there is aproblem with your indentation in the code

**Note on TABS and Spaces**
* both white spaces
* hard to visually tell def. 
* some editors don't show the diff

**Variable Name Errors**

* very common errors
* occurs when you try and use a variable that doesn't exist


```python
print(a)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-14-c5a4f3535135> in <module>()
    ----> 1 print(a)
    

    NameError: name 'a' is not defined


* usually tell us the var name doesn't exist
* Why does this occur?
* maybe you forgot to quote a string


```python
print(hello)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-15-43a14fcd4265> in <module>()
    ----> 1 print(hello)
    

    NameError: name 'hello' is not defined


* or forgot to create the variable before using it


```python
for number in range(10):
    count = count + number
print("The count is:" + str(count))
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-16-0654d41cd0f6> in <module>()
          1 for number in range(10):
    ----> 2     count = count + number
          3 print("The count is:" + str(count))


    NameError: name 'count' is not defined


* lastly you might have made  a typo
* let's say we fixed the above by adding the line `Count = 0` 
* you still get an error
* **remember** variables are case sensitive, so the var count is different from Count


```python
Count = 0
for number in range(10):
    count = count + number
print("The count is:" + str(count))
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-17-98d5c70d7ddc> in <module>()
          1 Count = 0
          2 for number in range(10):
    ----> 3     count = count + number
          4 print("The count is:" + str(count))


    NameError: name 'count' is not defined


** Item errors**

* errors dealing with containers
* trying to access an item in a list that doesn't exist



```python
letters = ['a', 'b', 'c']
print("Letter #1 is " + letters[0])
print("Letter #2 is " + letters[1])
print("Letter #3 is " + letters[2])
print("Letter #4 is " + letters[3])
```

    Letter #1 is a
    Letter #2 is b
    Letter #3 is c



    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-18-018869cdd091> in <module>()
          3 print("Letter #2 is " + letters[1])
          4 print("Letter #3 is " + letters[2])
    ----> 5 print("Letter #4 is " + letters[3])
    

    IndexError: list index out of range


* **IndexError** - meaning we tried to access a list index that did not exist

**File Errors** 
* errors dealing with reading and writing files


```python
file_handle = open('myfile.txt', 'r')
```


    ---------------------------------------------------------------------------

    FileNotFoundError                         Traceback (most recent call last)

    <ipython-input-19-f6e1ac4aee96> in <module>()
    ----> 1 file_handle = open('myfile.txt', 'r')
    

    FileNotFoundError: [Errno 2] No such file or directory: 'myfile.txt'


* ONE reason for reciving this error is that you specified an incorrect path to the file
* Eg. i'm in my folder 'python-novice-inflammation' and the file i tried to access is in another folder python-novice-inflammation/writing/myfile.txt, but I tried to open just 'myfile.txt'
* the correct path is python-novice-inflammation/writing/myfile.txt
* A related issue is we use the read flag instead of the write flag
* python will **not** give an error if you try and open a file for writing
* if you meant to open a file for reading, but accidentally opented it for writing, and then try and read from it, pytho will give an UnsupportedOPeration error


```python
file_handle = open('myfile', 'w')
file_handle.read()
```


    ---------------------------------------------------------------------------

    UnsupportedOperation                      Traceback (most recent call last)

    <ipython-input-21-9d0d96ff7714> in <module>()
          1 file_handle = open('myfile', 'w')
    ----> 2 file_handle.read()
    

    UnsupportedOperation: not readable



```python

```
