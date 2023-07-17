<h1>Time Complexity<h1>

<h2>Pattern # 1 -- Constant time<h2>

```python
def func(lst):
    return lst[1]
```
The time complexity of the function func is constant or O(1). It returns the element at index 1 of the input list lst. Regardless of the size of the list, the function always performs a single operation to access the element at a fixed position, so the time it takes to execute does not depend on the input size.


```python
def func():
  x = 1
  x += 1
  print(x)
```  
The time complexity of the fucntion is as follows:

* Line 1: x = 1
   * The assignment operation takes constant time, denoted as O(1).
* Line 2: x += 1
   * The operation invloves access, addition, variable assignment.The time complexity is denoted as O(3).
* Line 3: print(x)
   * The print function simply outputs the value of x to the console. Printing a single value is also a constant time operation, denoted as O(2).

The total time complexity is O(6) and as it is a constant, the fucntion will remain constant O(1).

The number of steps required to complete the function does not depend on the input size.




<h2>Pattern # 2 -- Linear time<h2>

```python
def loop(N):
    count = 0
    for _ in range(N):
        count += 1
    return count
```
The time complexity of the fucntion is as follows:

* Line 1: count = 0
  * The assignment operation takes constant time, denoted as O(1).
* Line 2: for _ in range(N):
  * This is a loop that iterates N times, where N is the input parameter. The values will assignment will aslo happen.The time complexity of the loop is O(2N), as the number of iterations directly depends on the value of N.
* Line 3: count += 1
  * The operation invloves access, addition, variable assignment and its in the loop it will run N times so the time complexity is O(3N).
* Line 4: return count
  * This statement will access the values and return. The return statement takes constant time, denoted as O(1+1).
* The total time complexity is O(1+2N+3N+2) = O(5N+3) removing constants O(N).  
* Single loop time complexity is O(N)


```python
def func(lst):
    # Assume lst is of length N
    lst.insert(0, 10)
```    
The time complexity of the fucntion is as follows:

* Line 1: lst.insert(0, 10)
  * In this method, insertion is happeneing at the beginning of the list. As this requires to insert the element in the beignning and move each element to the right one position. 
  * The time complexity of this is O(N), where N is the length of the list.




<h2>Pattern # 3 -- Quadratic Time<h2>

```python
def nested_loop(N):
    count = 0
    for _ in range(N):
        for _ in range(N):
            count += 1
    return count
```
The time complexity of the fucntion is as follows:

* Line 1: count = 0
  * The assignment operation takes constant time, denoted as O(1).
* Line 2: for _ in range(N):
  * This is a loop that iterates N times, where N is the input parameter. The values will assignment will aslo happen.The time complexity of the loop is O(2N), as the number of iterations directly depends on the value of N.
* Line 3: for _ in range(N):
  * This is a loop that iterates N * N times,as there are 2 loops where N is the input parameter. The time complexity is (2N*N)
* Line 4: count += 1
  * The operation invloves access, addition, variable assignment and its in the nested loop it will run N * N times so the time complexity is O(3N*N).
* Line 5: return count
  * This statement will access the values and return. The return statement takes constant time, denoted as O(1+1).
* The total time complexity is O(1+2N+2N^2+ 3N^2+2) = O(5N^2+2N+3) removing constants O(N^2). ( N*N is becuase of the loop inside the loop)  
* Nested loop time complexity is O(N^2)


Overall, the time complexity of the nested_loop function is O(N^2) because it contains nested loops, each with a time complexity of O(N). The total number of iterations is N^2, resulting in a quadratic time complexity.

```python
def nested_loop(lst):
    count = 0
    N = len(lst)
    for ele in range(N):
        lst.insert(0, ele)
```

The time complexity of the fucntion is as follows:

* Line 1: count = 0
  * The assignment operation takes constant time, denoted as O(1).
* Line 2: N = len(lst)
  *  This is an operation that calculates the length of the list lst and assign the value . It takes constant time, denoted as O(2).
* Line 3: for ele in range(N):
  * This is a loop that iterates N times, where N is the input parameter. The values will assignment will aslo happen.The time complexity of the loop is O(2N), as the number of iterations directly depends on the value of N.
* Line 4: lst.insert(0, ele)
  * The insert method is used to insert an element at the beginning of the list. and this insert is inside a for loop. This operation has a time complexity of O(N*N), where N is the length of the list. When an element is inserted at the beginning, all the existing elements need to be shifted one position to the right.
  * The total time complexity is O(1+2+2N+N^2) = O(N^2+2N+3) removing constants O(N^2). ( N*N is becuase of the loop inside the loop)  




<h2>Pattern # 4 -- Single loop with different step size<h2>

```python
def loop(N):
    for _ in range(N, 1, k):
        pass
```       
The time complexity of the fucntion is as follows:
* Line 1: for _ in range(N, 1, k):
  * This is a loop that iterates from N to 1, incrementing by k in each iteration. The time complexity of this loop depends on the values of N, k, and the number of iterations it performs.
  * The number of iterations in the loop can be calculated as (N - 1) // k + 1. It represents the number of times the loop will execute, taking into account the starting point N, the ending point 1, and the step size k.
  * The time complexity of the loop can be expressed as O((N - 1) // k + 1), which simplifies to O(N // k).
  * Therefore, the time complexity of the loop function depends on the values of N and k, and it can be represented as O(N // k).
  * After simplification O(N)
  
<h2>Pattern # 5 -- nested loops with different step size<h2>


```python
def func(N):
    for _ in range(N, 1, 3):
        for _ in range(N, 1, 2):
            pass
```
The time complexity of the fucntion is as follows:

* Line 1: for _ in range(N, 1, 3):
  * This is an outer loop that iterates from N to 1, with a step size of 3. The time complexity of this loop depends on the values of N and the number of iterations it performs. The number of iterations in the outer loop can be calculated as (N - 1) // 3 .
* Line 3: for _ in range(N, 1, 2):
  * This is an inner loop that also iterates from N to 1, with a step size of 2. Since it is nested inside the outer loop, it will be executed (N - 1) // 3 times for each iteration of the outer loop. The number of iterations in the inner loop can be calculated as (N - 1) // 2. Therefore, the total number of iterations is (N - 1) // 3 * [(N - 1) // 2].
* Therefore, the time complexity of the func function depends on the value of N, and it can be represented as O((N - 1) // 3 * (N - 1) // 2). After simplifications O(N^2)


<h2>Pattern # 6 --  Log N<h2>


```python
def func(N):
    i = 1
    count = 0
    factor = 2
    while (i < N):
        i *= factor
        count += 1
    return count 
```
The time complexity of the fucntion is as follows:

* Line 1: i = 1
  * This is a simple assignment operation that takes constant time, denoted as O(1).
* Line 2: count = 0
  * This is a simple assignment operation that takes constant time, denoted as O(1).
* Line 3: factor = 2
  * This is a simple assignment operation that takes constant time, denoted as O(1).
* Line 4: while (i < N):
  * This while loop continues as long as i is less than N. The number of iterations of the loop depends on the values of i and N.The variable i is multiplied by the factor 2 in each iteration of the loop. As long as i remains less than N, the loop will execute and i will be updated.   
  * As the valriable i is not incremented linearly and its multiplied by 2 all the time. You are not skipping every other, rather the multiplication is making you skip lots more, so follows log N behavior
  * Time complexity is O(log N)  
* Line 5: count += 1
  * The operation invloves access, addition, variable assignment and its in the nested loop it will run N * N times so the time complexity is O(3Log N).
* Line 6: return count
  * This statement will access the values and return. The return statement takes constant time, denoted as O(1+1).
*  The total time complexity is O(1+1+1+Log N +3Log N+ 2) = O(4 Log N +5) removing constants O(Log N).
