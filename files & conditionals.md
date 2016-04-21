
We now have almost everything we need to process our data files, only thing missing is a library to grab files


```python
import glob
import numpy
```

* glob contains function glob that finds files that match a pattern
* `*` matches 0+ characters; `?` matches any one char


```python
print(glob.glob('data/inflammation*.csv'))
```

    ['data/inflammation-01.csv', 'data/inflammation-02.csv', 'data/inflammation-03.csv', 'data/inflammation-04.csv', 'data/inflammation-05.csv', 'data/inflammation-06.csv', 'data/inflammation-07.csv', 'data/inflammation-08.csv', 'data/inflammation-09.csv', 'data/inflammation-10.csv', 'data/inflammation-11.csv', 'data/inflammation-12.csv']


* results in a list of strings, we can loop oer
* we want to create sets of plots


```python
%matplotlib inline
```


```python
import numpy
import matplotlib.pyplot

filenames = glob.glob('data/inflammation*.csv')
filenames = filenames[0:3]
for f in filenames:
    print(f)
    
    data = numpy.loadtxt(fname = f, delimiter=',')
    
    fig = matplotlib.pyplot.figure(figsize=(10.0,3.0))
    
    axes1 = fig.add_subplot(1,3,1)
    axes2 = fig.add_subplot(1,3,2)
    axes3 = fig.add_subplot(1,3,3)
    
    axes1.set_ylabel('average')
    axes1.plot(data.mean(axis=0))
    
    axes2.set_ylabel('max')
    axes2.plot(data.max(axis=0))
    
    axes3.set_ylabel('min')
    axes3.plot(data.min(axis=0))
    
    fig.tight_layout()
    matplotlib.pyplot.show(fig)
```

    data/inflammation-01.csv



![png](files%20%26%20conditionals_files/files%20%26%20conditionals_6_1.png)


    data/inflammation-02.csv



![png](files%20%26%20conditionals_files/files%20%26%20conditionals_6_3.png)


    data/inflammation-03.csv



![png](files%20%26%20conditionals_files/files%20%26%20conditionals_6_5.png)


We can ask Python to take different actions, depending on a condition, with an if statement:

## Making choices

* last lesson we discovereed something suspicious in our inflammatin data by drawing plots
* how can python recognized these different features and act on it
* we will write code that runs on certain conditions


```python
#We use an if statement to take different actions 
#based on conditions
num = 37
if num > 100:
    print('greater')
else:
    print('not greater')
print('done')
```

    not greater
    done


* second line of code above uses keyword `if` to denote choice
* if the test after `if` is true, the body of the `if` are executed
* if test false the body `else` is executed
* conditional statements don't have to include `else` - if not present python does nothing


```python
num = 53
print('before conditional...')
if num > 100:
    print('53 is greater than 100')
print('...after conditional')
```

    before conditional...
    ...after conditional


we can also chain several tests together using `elif`, short for `else if`



```python
num = -3

if num > 0:
    print(num, "is positive")
elif num == 0:
    print(num, "is zero")
else:
    print(num, "is negative")
```

    -3 is negative


* NOTE: we use `==` to test for equality rather than single equal b/c the later is the assignment operator
* we can also combine tests using `and` and `or`. `and` is only true if both parts are true


```python
if (1 > 0) and (-1 > 0):
    print('both parts are true')
else:
    print('at least one part is false')
```

    at least one part is false


while `or` is true if at least one part is true:


```python
if (1 < 0) or (-1 < 0):
    print('at least one test is true')
```

    at least one test is true


## Challenge - making choices:

Which of the following would be printed if you were to run this code? Why did you pick this answer?

A
B
C
B and C

```python
if 4 > 5:
    print('A')
elif 4 == 5:
    print('B')
elif 4 < 5:
    print('C')
```


```python
if 4 > 5:
    print('A')
elif 4 == 5:
    print('B')
elif 4 < 5:
    print('C')
```

    C


### Checking out data

* we can use conditionals to check for suspcioious features in our datat
* first 2 plots mzx inflamm per day seemed to rise in straight line
* we can chek for this inside the `for` loop 


```python
if data.max(axis=0)[0] == 0 and data.max(axis=0)[20] == 20:
    print('Suspicious looking maxima!')
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-12-b8646b1001c4> in <module>()
    ----> 1 if data.max(axis=0)[0] == 0 and data.max(axis=0)[20] == 20:
          2     print('Suspicious looking maxima!')


    NameError: name 'data' is not defined


* let's check for the minima like we saw on third day (flat)


```python
elif data.min(axis=0).sum() == 0:
    print('Minima add up to zero!')
```

* if nether of the conditions are met we can use `else` for all clear


```python
else:
    print('seems OK!')
```

let's test! 


```python
data = numpy.loadtxt(fname='data/inflammation-01.csv', delimiter=',')
if data.max(axis=0)[0] == 0 and data.max(axis=0)[20] == 20:
    print('Suspicious looking maxima!')
elif data.min(axis=0).sum() == 0:
    print('Minima add up to zero!')
else:
    print('Seems OK!')
```

    Suspicious looking maxima!



```python
data = numpy.loadtxt(fname='data/inflammation-03.csv', delimiter=',')
if data.max(axis=0)[0] == 0 and data.max(axis=0)[20] == 20:
    print('Suspicious looking maxima!')
elif data.min(axis=0).sum() == 0:
    print('Minima add up to zero!')
else:
    print('Seems OK!')
```

    Minima add up to zero!


asked python to do something depending on diff conditions; we can also imaging not using the `else` so messages are only printed whens omething is wrong

## Challenge - making choices 2:

True and False are special words in Python called booleans which represent true and false statements. However, they aren’t the only values in Python that are true and false. In fact, any value can be used in an if or elif. After reading and running the code below, explain what the rule is for which values are considered true and which are considered false.

```python
if '':
    print('empty string is true')
if 'word':
    print('word is true')
if []:
    print('empty list is true')
if [1, 2, 3]:
    print('non-empty list is true')
if 0:
    print('zero is true')
if 1:
    print('one is true')
```


```python
if '':
    print('empty string is true')
if 'word':
    print('word is true')
if []:
    print('empty list is true')
if [1, 2, 3]:
    print('non-empty list is true')
if 0:
    print('zero is true')
if 1:
    print('one is true')
```

    word is true
    non-empty list is true
    one is true



```python

```
