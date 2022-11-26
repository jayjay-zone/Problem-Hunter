# itertools없이 구현하기

premutation과 combination은 기본적으로 재귀적인 성질을 가지고 있다.

### permutation

예를 들어, arr = [1,2,3], n=3일 때의 permutation을 구해보자

permutation의 경우를 첫번쨰 오는 수로 나눠보면,
1. 1이 가장 첫번째 오는 경우
    - [1,2,3] [1,3,2]
2. 2가 가장 첫번째 오는 경우
    - [2,1,3] [2,3,1]
3. 3가 가장 첫번째 오는 경우
    - [3,1,2] [3,2,1]

1이 가장 첫번째 오는 경우 [2,3]과 [3,2]가 이어지는데,
이는 [2,3]의 permutation과 동일하다

이를 공식으로 나타내면, 

permutation([1,2,3], 3) = [1,permutation([2,3], 2)] +  [2,permutation([1,3],2)] +  [3,permutation([2,1], 2)] 




이를 재귀함수로 구현해자.

명심할 것은, 재귀함수에는 꼭 **초기값**이 들어가야 한다는 것이다.


```python
def permutation(arr, n):
    assert n <= len(arr)
    result = []
    
    if n == 0:
        return [[]]
    
    for i in range(len(arr)):
        res_arr = [arr[i]]
        for p in permutation(arr[:i]+arr[i+1:], n-1):
            result +=[res_arr+p]
    return result
            
```


```python
permutation([1,2,3], 2)
```




    [[1, 2], [1, 3], [2, 1], [2, 3], [3, 1], [3, 2]]



### combination

예를 들어, arr = [0,1,2,3], n=2일 때의 combination 구해보자

combination 경우, 순서를 고려하지 않기 때문에, 반드시 들어가는 원소를 정하는 방식으로 경우를 나눠본다
1. 0이 꼭 들어가는 경우
    - [0,1][0,2][0,3]
    - [0] + [1,2,3]에서 1개를 고르는 방법
2. 1이 꼭 들어가는 경우
    - [1,2][1,3]
    - [1] + [2,3]에서 1개를 고르는 방법
    - 앞에서 0이 꼭 들어가는 경우를 고려했으므로, 0,1을 뺀 나머지 수열에서 1개를 고른다
3. 2가 꼭 들어가는 경우
    - [2,3]
    - [2] + [3]에서 1개를 고르는 방법
    - 0,1,2를 뺀 나머지 수열에서 1개를 고른다


```python
def gen_combinations(arr, n):
    result =[] 

    if n == 0: 
        return [[]]

    for i in range(0, len(arr)): 
        elem = arr[i] 
        rest_arr = arr[i + 1:] 
        for C in gen_combinations(rest_arr, n-1): 
            result.append([elem]+C) 
              
    return result

```


```python
gen_combinations([0,1],1)
```




    [[0], [1]]




```python

```


```python

```
