
## Defensive programming


**We've covered:**

* variables and lists,
* file i/o,
* loops,
* conditionals,
* and functions

**but we haven't shown whether a program is getting the right answer and whether it is still getting the right answers as we change the program**

We need to: 

* write prgrams that check for their own operation
* write and run tests for widely-used functions
* make sure we know what 'correct' actually means

* as with real carpentry - time is saved by carefully measuring before cutting wood

1. assume errors will happen and guard against them
2. Called defensive programming 
3. we add assertions to our code so that it checks itself as it runs 
4. Python will evaluate assertions, if true does nothing, if false halts and prints error

** for example**


```python
numbers = [1.5, 2.3, 0.7, -0.001, 4.4]
total = 0.0
for n in numbers:
    assert n > 0.0, 'Data should only contain positve values'
    total += n
print('total is: ', total)
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-2-ef07ff366dc5> in <module>()
          2 total = 0.0
          3 for n in numbers:
    ----> 4     assert n > 0.0, 'Data should only contain positve values'
          5     total += n
          6 print('total is: ', total)


    AssertionError: Data should only contain positve values


* Programs like firefox browser are full of assertions: 10-20% (to check that 80-90% are worksing correctly)
* Three assertion categories:
    1. a precondition -- something that must be true at the of the fuction in order for it work correctly
    2. a postcondition - somthing that the function guarantees is true after execution
    3. invariant - somthing that is always true at a particular point in code


* Suppose we are representing rectangles using a tuple of four coordinates (x0,y0,x1,y2) representing the lower left and upper right corners of the rectangle. 
* IN order to do some calculations, we need to normalize the rectangle so that the lower left corner is at the origin and the longest side is 1.0 units long.
* The following function does that, but also checks that its input is correctly formatted and that its result makes sense:


```python
def normalize_rectangle(rect):
    '''Normalizes a rectangle so that it is at the origin and 1.0 units long on its longest axis.'''
    assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
    x0, y0, x1, y1 = rect
    assert x0 < x1, 'Invalid X coordinates'
    assert y0 < y1, 'Invalid Y coordinates'

    dx = x1 - x0
    dy = y1 - y0
    if dx > dy:
        scaled = float(dx) / dy
        upper_x, upper_y = 1.0, scaled
    else:
        scaled = float(dx) / dy
        upper_x, upper_y = scaled, 1.0

    assert 0 < upper_x <= 1.0, 'Calculated upper X coordinate invalid'
    assert 0 < upper_y <= 1.0, 'Calculated upper Y coordinate invalid'

    return (0, 0, upper_x, upper_y)
```


```python
print(normalize_rectangle((0.0, 1.0, 2.0))) #missing the fourth coordinate
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-5-e5e9b0361026> in <module>()
    ----> 1 print(normalize_rectangle((0.0, 1.0, 2.0))) #missing the fourth coordinate
    

    <ipython-input-4-9f8adbfdcfc9> in normalize_rectangle(rect)
          1 def normalize_rectangle(rect):
          2     '''Normalizes a rectangle so that it is at the origin and 1.0 units long on its longest axis.'''
    ----> 3     assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
          4     x0, y0, x1, y1 = rect
          5     assert x0 < x1, 'Invalid X coordinates'


    AssertionError: Rectangles must contain 4 coordinates


* now look at the post-conditions to help us catch bugs by telling us the calculation isn't right
* for example if we normalize a rect that is taller than it is wide


```python
print(normalize_rectangle((0.0,0.0, 1.0, 5.0)))
```

    (0, 0, 0.2, 1.0)



```python
print(normalize_rectangle((0.0,0.0,5.0,1.0)))
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-8-b091cc887afe> in <module>()
    ----> 1 print(normalize_rectangle((0.0,0.0,5.0,1.0)))
    

    <ipython-input-4-9f8adbfdcfc9> in normalize_rectangle(rect)
         16 
         17     assert 0 < upper_x <= 1.0, 'Calculated upper X coordinate invalid'
    ---> 18     assert 0 < upper_y <= 1.0, 'Calculated upper Y coordinate invalid'
         19 
         20     return (0, 0, upper_x, upper_y)


    AssertionError: Calculated upper Y coordinate invalid


* re-reading our function, we realize that line 10 should divide dy by dx rather than dx by dy
* if we had left out hte assertion at the end of the function we would have created and returned somethign that had the right shape as a valid answer but wasn't
* assertions are just about catching errors they also help people understand programs (chance to check their understanding)
* good programmers follow: 1) fail early, fail often - catch mistakes as early as possible 2) turn bugs into assertions or tests - whenever you fix a bug write an assertion, so you won't make same mistake later (regression)

## TDD 

* assertion checks that something is true at a particular point, 
* next step is check overall behavior of piece of code
* for instance we need to find the overlap for two or more time series - lines of time intervals
* most novices would: write function range_overlap, call it interactively on two or three diff inputs, fix if wrong
* better way: write a short function for each test, write a `range_overlap` function that should pass tests, if `range_overlap` fails, fix it and re-run test function

* writing tests bfore the function is called text driven devlopment
* its advocates belive it produces better coder faster because:
    1. confirmation bias encroaches if one writes tests after you write the function (subconsciously write to pass)
    2. writing test helps programmers figure out what teh function is actually supposed to do

here are three test functions for range_overlap:


```python
assert range_overlap([ (0.0, 1.0) ]) == (0.0, 1.0)
assert range_overlap([ (2.0, 3.0), (2.0, 4.0) ]) == (2.0, 3.0)
assert range_overlap([ (0.0, 1.0), (0.0, 2.0), (-1.0, 1.0) ]) == (0.0, 1.0)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-9-d8be150fbef6> in <module>()
    ----> 1 assert range_overlap([ (0.0, 1.0) ]) == (0.0, 1.0)
          2 assert range_overlap([ (2.0, 3.0), (2.0, 4.0) ]) == (2.0, 3.0)
          3 assert range_overlap([ (0.0, 1.0), (0.0, 2.0), (-1.0, 1.0) ]) == (0.0, 1.0)


    NameError: name 'range_overlap' is not defined


* error is reassuring b/c we haven't written that fuction!
* b/c we wrote the assertions, we have defined what our input and output should look like!
* we are missing a case where the ranges don't overlap


```python
assert range_overlap([ (0.0, 1.0), (5.0, 6.0) ]) == ???
```


      File "<ipython-input-10-cf12f48f208b>", line 1
        assert range_overlap([ (0.0, 1.0), (5.0, 6.0) ]) == ???
                                                            ^
    SyntaxError: invalid syntax




```python

```
