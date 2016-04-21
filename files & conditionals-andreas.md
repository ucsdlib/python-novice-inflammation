
We now have almost everything we need to process our data files, only thing missing is a library to grab files


```python
import glob
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



![png](files%20%26%20conditionals-andreas_files/files%20%26%20conditionals-andreas_6_1.png)


    data/inflammation-02.csv



![png](files%20%26%20conditionals-andreas_files/files%20%26%20conditionals-andreas_6_3.png)


    data/inflammation-03.csv



![png](files%20%26%20conditionals-andreas_files/files%20%26%20conditionals-andreas_6_5.png)


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

```


```python
num= 37
if num > 100:
    print("num is greater than 100")
else:
    print("num is less than 100")
print('done')
```

    num is less than 100
    done


* using elif -- else if to test for equal to 37
* == is equality, = an assignment
* see below


```python
num= 37
if num > 100:
    print("num is greater than 100")
elif num == 37:
    print("number is 37")
else:
    print("num is less than 100")
print('done')
```

    number is 37
    done



```python
num= 137
if num > 100:
    print("num is greater than 100")
elif num == 37:
    print("number is 37")
else:
    print("num is less than 100")
print('done')
```

    num is greater than 100
    done



```python
num= 27
if num > 100:
    print("num is greater than 100")
elif num == 37:
    print("number is 37")
else:
    print("num is less than 100")
print('done')
```

    num is less than 100
    done



```python
word = "giraffe"
if len(word) >= 20:
    print(len(word))
else:
    print(word)
```

    giraffe



```python
word = "giraffe"
if word == "elephant":
    print(len(word))
else:
    print(word)
```

    giraffe



```python

```
