# Python_Sorting arithmetic
## Top Interview
- [1.Bubble Sort](#2bubble-sort)  
- [2.Quick Sort](#3quick-sort)  
- [3.Insert Sort](#4insert-sort)  
- [4.Selection Sort](#5.selection-sort)  
- [5.Shell Sort](#6shell-sort) 
- [6.Merge Sort](#7merge-sort) 
- [7.Heap Sort](#8heap-sort) 
- [8.Counting Sort](#8counting-sort) 
- [9.Bucket Sort](#8bucket-sort) 
- [10.Radix Sort](#8radix-sort) 
### 1.Bubble Sort
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
"""""""""TEST"""""""""""""
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
### 2.Quick Sort
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
"""""""""TEST"""""""""""""
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
### 3.Insert Sort
插入排序：Insert Sort简单排序---平均时间复杂度O(n^2)---空间复杂度O(1)---稳定
算法步骤:
将第一待排序序列第一个元素看做一个有序序列，把第二个元素到最后一个元素当成是未排序序列。2. 从头到尾依次扫描未排序序列，将扫描到的每个元素插入有序序列的适当位置。（如果待插入的元素与有序序列中的某个元素相等，则将待插入元素插入到相等元素的后面。）
```python
def insertionSort(arr):
    for i in range(len(arr)):
        preIndex = i-1
        current = arr[i]
        while preIndex >= 0 and arr[preIndex] > current:
            arr[preIndex+1] = arr[preIndex]
            preIndex-=1
        arr[preIndex+1] = current
    return arr
"""""""""TEST"""""""""""""
print("<<< Insert Sort >>>")
x=input("请输入待排序数列:\n")
y=x.split()
array=[]
for i in y:
    array.append(int(i))
array=insertionSort(array)
#print array
print("数列按序排列如下：")
for i in array:
    print(i,end=' ')
```
### 4.Selection Sort
Selection Sort选择排序---平均时间复杂度O(n^2)---空间复杂度O(1)---不稳定
##算法步骤:
1.首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置
2.再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。
3.重复第二步，直到所有元素均排序完毕。
```python
def selectionSort(arr):
    for i in range(len(arr) - 1):
        # 记录最小数的索引
        minIndex = i
        for j in range(i + 1, len(arr)):
            if arr[j] < arr[minIndex]:
                minIndex = j
        # i 不是最小数时，将 i 和最小数进行交换
        if i != minIndex:
            arr[i], arr[minIndex] = arr[minIndex], arr[i]
    return arr
"""""""""TEST"""""""""""""
print("<<< Selection Sort >>>")
x=input("请输入待排序数列:\n")
y=x.split()
array=[]
for i in y:
    array.append(int(i))
array=selectionSort(array)
#print array
print("数列按序排列如下：")
for i in array:
    print(i,end=' ')
```
### 5.Shell Sort
Shell Sort希尔排序---平均时间复杂度O(nLogn)---空间复杂度O(1)---不稳定
希尔排序，也称递减增量排序算法，是插入排序的一种更高效的改进版本。但希尔排序是非稳定排序算法。
算法步骤:
1.选择一个增量序列 t1，t2，……，tk，其中 ti > tj, tk = 1；
2.按增量序列个数 k，对序列进行 k 趟排序；
3.每趟排序，根据对应的增量 ti，将待排序列分割成若干长度为 m 的子序列，分别对各子表进行直接插入排序。仅增量因子为 1 时，整个序列作为一个表来处理，表长度即为整个序列的长度。
```python
import math
def shellSort(arr):
    gap=1
    while(gap < len(arr)/3):
        gap = gap*3+1
    while gap > 0:
        for i in range(gap,len(arr)):
            temp = arr[i]
            j = i-gap
            while j >=0 and arr[j] > temp:
                arr[j+gap]=arr[j]
                j-=gap
            arr[j+gap] = temp
        gap = math.floor(gap/3)
    return arr
"""""""""TEST"""""""""""""
print("<<< Shell Sort >>>")
x=input("请输入待排序数列:\n")
y=x.split()
array=[]
for i in y:
    array.append(int(i))
array=shellSort(array)
#print array
print("数列按序排列如下：")
for i in array:
    print(i,end=' ')
```
### 6.Merge Sort
Merge Sort归并排序---平均时间复杂度O(nLogn)---空间复杂度O(n)---稳定
归并排序（Merge sort）是建立在归并操作上的一种有效的排序算法。该算法是采用分治法（Divide and Conquer）的一个非常典型的应用。
算法步骤：
1.申请空间，使其大小为两个已经排序序列之和，该空间用来存放合并后的序列；
2.设定两个指针，最初位置分别为两个已经排序序列的起始位置；
3.比较两个指针所指向的元素，选择相对小的元素放入到合并空间，并移动指针到下一位置；
4.重复步骤 3 直到某一指针达到序列尾；
5.将另一序列剩下的所有元素直接复制到合并序列尾。
```python
def mergeSort(arr):
    if(len(arr)<2):
        return arr
    middle = math.floor(len(arr)/2)
    left, right = arr[0:middle], arr[middle:]
    return merge(mergeSort(left), mergeSort(right))

def merge(left,right):
    result = []
    while left and right:
        if left[0] <= right[0]:
            result.append(left.pop(0));
        else:
            result.append(right.pop(0));
    while left:
        result.append(left.pop(0));
    while right:
        result.append(right.pop(0));
    return result
"""""""""TEST"""""""""""""
print("<<< Merge Sort >>>")
x=input("请输入待排序数列:\n")
y=x.split()
array=[]
for i in y:
    array.append(int(i))
array=mergeSort(array)
#print array
print("数列按序排列如下：")
for i in array:
    print(i,end=' ')
```
### 7.Heap Sort
HeapSort堆排序---平均时间复杂度O(nLogn)---空间复杂度O(1)---不稳定
堆排序（Heapsort）是指利用堆这种数据结构所设计的一种排序算法。堆积是一个近似完全二叉树的结构，并同时满足堆积的性质：即子结点的键值或索引总是小于（或者大于）它的父节点。
1.大顶堆：每个节点的值都大于或等于其子节点的值，在堆排序算法中用于升序排列；
2.小顶堆：每个节点的值都小于或等于其子节点的值，在堆排序算法中用于降序排列；
算法步骤：
1.创建一个堆 H[0……n-1]；
2.把堆首（最大值）和堆尾互换；
3.把堆的尺寸缩小 1，并调用 shift_down(0)，目的是把新的数组顶端数据调整到相应位置；
4.重复步骤 2，直到堆的尺寸为 1。
```python
def buildMaxHeap(arr):
    import math
    for i in range(math.floor(len(arr)/2),-1,-1):
        heapify(arr,i)

def heapify(arr, i):
    left = 2*i+1
    right = 2*i+2
    largest = i
    if left < arrLen and arr[left] > arr[largest]:
        largest = left
    if right < arrLen and arr[right] > arr[largest]:
        largest = right

    if largest != i:
        swap(arr, i, largest)
        heapify(arr, largest)

def swap(arr, i, j):
    arr[i], arr[j] = arr[j], arr[i]

def heapSort(arr):
    global arrLen
    arrLen = len(arr)
    buildMaxHeap(arr)
    for i in range(len(arr)-1,0,-1):
        swap(arr,0,i)
        arrLen -=1
        heapify(arr, 0)
    return arr
"""""""""TEST"""""""""""""
print("<<< HeapSort >>>")
x=input("请输入待排序数列:\n")
y=x.split()
array=[]
for i in y:
    array.append(int(i))
array=heapSort(array)
#print array
print("数列按序排列如下：")
for i in array:
    print(i,end=' ')
```
### 8.Counting Sort
CountingSort计数排序---平均时间复杂度O(n+k)---空间复杂度O(k)---稳定
计数排序的核心在于将输入的数据值转化为键存储在额外开辟的数组空间中。作为一种线性时间复杂度的排序，计数排序要求输入的数据必须是有确定范围的整数。
```python
def countingSort(arr, maxValue):
    bucketLen = maxValue+1
    bucket = [0]*bucketLen
    sortedIndex =0
    arrLen = len(arr)
    for i in range(arrLen):
        if not bucket[arr[i]]:
            bucket[arr[i]]=0
        bucket[arr[i]]+=1
    for j in range(bucketLen):
        while bucket[j]>0:
            arr[sortedIndex] = j
            sortedIndex+=1
            bucket[j]-=1
    return arr
```
### 9.Bucket Sort
BucketSort桶排序---平均时间复杂度O(n+k)---空间复杂度O(n+k)---稳定
桶排序实际上是计数排序的推广，但实现上要复杂许多。桶排序先用一定的函数关系将数据划分到不同有序的区域（桶）内，然后子数据分别在桶内排序，之后顺次输出。当每一个不同数据分配一个桶时，也就相当于计数排序.
假设n个数据，划分为k个桶，桶内采用快速排序，时间复杂度为O(n)+O(k * n/k*log(n/k))=O(n)+O(n*(log(n)-log(k))),
显然，k越大，时间复杂度越接近O(n)，当然空间复杂度O(n+k)会越大，这是空间与时间的平衡。
```python
def BucketSort(ls):
    ##############桶内使用快速排序
    def QuickSort(ls):
        def partition(arr,left,right):
            key=left         #划分参考数索引,默认为第一个数，可优化
            while left<right:
                while left<right and arr[right]>=arr[key]:
                    right-=1
                while left<right and arr[left]<=arr[key]:
                    left+=1
                (arr[left],arr[right])=(arr[right],arr[left])
            (arr[left],arr[key])=(arr[key],arr[left])
            return left
 
        def quicksort(arr,left,right):   #递归调用
            if left>=right:
                return
            mid=partition(arr,left,right)
            quicksort(arr,left,mid-1)
            quicksort(arr,mid+1,right)
        #主函数
        n=len(ls)
        if n<=1:
            return ls
        quicksort(ls,0,n-1)
        return ls
    ######################
    n=len(ls)
    big=max(ls)
    num=big//10+1
    bucket=[]
    buckets=[[] for i in range(0,num)]
    for i in ls:
        buckets[i//10].append(i)     #划分桶
    for i in buckets:                       #桶内排序
        bucket=QuickSort(i)
    arr=[]
    for i in buckets:
        if isinstance(i, list):
            for j in i:
                arr.append(j)
        else:
            arr.append(i)
    for i in range(0,n):
        ls[i]=arr[i]
    return ls
"""""""""TEST"""""""""""""
print("Bucket Sort")
x=input("请输入待排序数列：\n")
y=x.split()
arr=[]
for i in  y:print("<<< Quick Sort >>>")
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
    arr.append(int(i))
arr=BucketSort(arr)
#print(arr)
print("数列按序排列如下：")
for i in arr:
    print(i,end=' ')
```
### 10.Radix Sort
RadixSort基数排序---平均时间复杂度O(n*k)---空间复杂度O(n+k)---稳定
基数排序进行多轮按位比较排序，轮次取决于最大数据值的位数。先按照个位比较排序，然后十位百位以此类推，优先级由低到高，这样后面的移动就不会影响前面的。基数排序按位比较排序实质上也是一种划分，一种另类的‘桶’罢了。比如，第一轮按各个位比较，按个位大小排序分别装入10个‘桶’中，‘桶’中个位相同的数据视作相等，桶是有序的，按序输出，后面轮次接力完成排序。
基数排序‘桶’内数据在划分桶时便已排序O(n)，k个桶，时间复杂度为O(n*k)。额外空间开销出在数据划分入桶过程，桶大小O(n+k)，空间复杂度O(n+k)。
```python
import math
def RadixSort(ls):
    def getbit(x,i):       #返回x的第i位（从右向左，个位为0）数值
        y=x//pow(10,i)
        z=y%10
        return z
    def CountSort(ls):
        n=len(ls)
        num=max(ls)
        count=[0]*(num+1)
        for i in range(0,n):
            count[ls[i]]+=1
        arr=[]
        for i in range(0,num+1):
            for j in range(0,count[i]):
                arr.append(i)
        return arr
    Max=max(ls)
    for k in range(0,int(math.log10(Max))+1):             #对k位数排k次,每次按某一位来排
        arr=[[] for i in range(0,10)]
        for i in ls:                 #将ls（待排数列）中每个数按某一位分类（0-9共10类）存到arr[][]二维数组（列表）中
            arr[getbit(i,k)].append(i)
        for i in range(0,10):         #对arr[]中每一类（一个列表）  按计数排序排好
            if len(arr[i])>0:
                arr[i]=CountSort(arr[i])
        j=9
        n=len(ls)
        for i in range(0,n):     #顺序输出arr[][]中数到ls中，即按第k位排好
            while len(arr[j])==0:
                j-=1
            else:
                ls[n-1-i]=arr[j].pop()   
    return ls
"""""""""TEST"""""""""""""
print("RadixSort")
x=input("请输入待排序数列：\n")
y=x.split()
arr=[]
for i in  y:
    arr.append(int(i))
arr=RadixSort(arr)
#print(arr)
print("数列按序排列如下：")
for i in arr:
    print(i,end=' ') 
```
