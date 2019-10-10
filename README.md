# Python_Sorting arithmetic
## Top Interview
- [1.Bubble Sort](#2bubble-sort)  
- [2.Quick Sort](#3quick-sort)  
- [3.get all IPO companies from 2010 to 2018 via NASDAQ](#4get-all-IPO-companies-from-2010-to-2018-via-NASDAQ)  
- [4.spliting](#5.spliting)  
- [5.fetch data from S-1 form SEC](#6fetch-data-from-S-1-form-SEC) 
- [6.fetch P/E ratio from yahoo and NASDAQ](#7fetch-P/E-ratio-from-yahoo-and-NASDAQ) 
- [7.get current stock price](#8get-current-stock-price) 
- [8.get current stock price](#8get-current-stock-price) 
- [9.get current stock price](#8get-current-stock-price) 
- [10.get current stock price](#8get-current-stock-price) 
### 2.Bubble Sort
交换排序：Bubble Sort冒泡排序---平均时间复杂度O(n^2)---空间复杂度O(1)---稳定
```python
def bubblesort(ls):
    n=len(ls)
    if n<=1:
        return ls
    for i in range(0,n):
        for j in range(0,n-i-1):
            if ls[j]>ls[j+1]:
                (ls[j],ls[j+1])=(ls[j+1],ls[j])
    return ls
``````````````````````````````````````````````````````````````````````````````````````````````````````````````````````````
print("<<< Bubble Sort >>>")
x=input("请输入待排序数列:\n")
y=x.split()
array=[]
for i in y:
    array.append(int(i))
array=bubblesort(array)
#print array
print("数列按序排列如下：")
for i in array:
    print(i,end=' ')
```
### 3.Quick Sort
交换排序：Quick Sort快速排序---平均时间复杂度O(nlog2(n))---空间复杂度O(nlog2(n))---不稳定
```python
def quicksort(arr):
    """快速排序"""
    if len(arr) < 2:
        return arr
    # 选取基准，随便选哪个都可以，选中间的便于理解
    mid = arr[len(arr) // 2]
    # 定义基准值左右两个数列
    left, right = [], []
    # 从原始数组中移除基准值
    arr.remove(mid)
    for item in arr:
        # 大于基准值放右边
        if item >= mid:
            right.append(item)
        else:
            # 小于基准值放左边
            left.append(item)
    # 使用迭代进行比较
    return quicksort(left) + [mid] + quicksort(right)

print("<<< Quick Sort >>>")
x=input("请输入待排序数列:\n")
y=x.split()
array=[]
for i in y:
    array.append(int(i))
array=quicksort(array)
#print array
print("数列按序排列如下：")
for i in array:
    print(i,end=' ')
```
