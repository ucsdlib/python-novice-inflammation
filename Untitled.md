

```python
element = 'oxygen'
```


```python
element[-3:-1]
```




    'ge'




```python
element[-1:-3]
```




    ''




```python
element[5:2:-1]
```




    'neg'




```python
for num in range(1,4):
    print(num)
```

    1
    2
    3



```python
product = 1
base = 5
for number in range(3):
    product = product * base
print(product)
```

    125



```python
result = 1
for num in range(3):
    result = result * 5
print(result)
```

    125



```python
word = 'Newton'
position = 0
new_word = ''
for char in word:
    position = position - 1
    print(word[position])
```

    n
    o
    t
    w
    e
    N



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
odds = [1,3,5,7]
```


```python
print('odds are:', odds)
```

    odds are: [1, 3, 5, 7]



```python
print('first and last:', odds[0], odds[-1])
```

    first and last: 1 7



```python
for number in odds:
    print(number)
```

    1
    3
    5
    7



```python
names = ['Newton', 'Darwing', 'Turing']
print('names is originally', names)
names[1] = 'Darwin'
print(names)
```

    names is originally ['Newton', 'Darwing', 'Turing']
    ['Newton', 'Darwin', 'Turing']



```python
name = 'Bell'
name[0] = 'b'
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-19-220df48aeb2e> in <module>()
          1 name = 'Bell'
    ----> 2 name[0] = 'b'
    

    TypeError: 'str' object does not support item assignment



```python
name = 'bell'
```


```python
names[1][0]
```




    'D'




```python
names
```




    ['Newton', 'Darwin', 'Turing']




```python
names2 = names
```


```python
names2
```




    ['Newton', 'Darwin', 'Turing']




```python
names2[1] = 'darwin'
```


```python
names2
```




    ['Newton', 'darwin', 'Turing']




```python
names
```




    ['Newton', 'darwin', 'Turing']




```python

```
