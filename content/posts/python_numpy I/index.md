---
title: "Python - NumPy 創建與使用方法"
description: ""
date: 2021-07-13
draft: false
categories: 
- Data Analytics
tags:
- Python Numpy
cover:
    image: "cover.jpeg"
    relative: true
---

## 前言

在資料科學中，我們常常需要面對大量的資料來進行資料的加工、運算及分析，為了有效率的對資料進行各式各樣的處理，我們常常會匯入 Python 的套件來使用，以減少在資料處理過程中繁複的程式碼。

<!--more-->

經常使用的函式庫如 Numpy、Scipy、Pandas、以及 Matplotlib ，這四種是在資料進行預處理以及資料視覺化時非常方便的工具。其中， Numpy 是 Pandas、SciPy、Scikit learn 等相關套件的重要基礎，對於往後學習其他資料科學相關套件會非常有幫助。

那這篇主要會針對 Numpy 的基礎方法進行介紹。事不宜遲，就開始吧。

## 一、NumPy 的認識

NumPy 是 Numerical Python 的縮寫，底層以 C 和 Fortran 語言實作，是科學計算與資料科學的套件，不僅能夠處理維度陣列與矩陣的運算，針對陣列的運算也提供大量的數學函式函式庫，且處理速度非常的快速，它具有以下幾個重要特色：

- 提供高效能的多維度陣列數學函式庫
- 可以整合 C/C++ 及 Fortran 的程式碼
- 具備同值資料型態的特性
- 具平行處理能力來快速操作陣列
- 利用 NumPy Array 替代 Python List

### 1. 安裝

在使用 Python 第三方的函式庫時，我們可以在終端機透過 pip(Python Package Index) 的指令來安裝 Numpy，如果使用的是 Python 3.x 的版本則使用 pip3 進行安裝。

```python
pip3 install numpy
```

### 2. 匯入

並透過 import 匯入 Numpy ，而下方的 np 是可以自由指定的名稱，可以使用 as 來進行指定，慣例上會使用套件名稱的縮寫。

```python
import numpy as np
```

### 3. Ndarray 與 List

ndarray (陣列) 一個非常類似於 list (串列) 的序列型態 ，實際上 ndarray 是 Numpy 的陣列資料型態，而 list 則是 Python 內建的資料型態。

ndarray 和 list 最大的不同在於，list 具備了儲存異質資料型態的特性，在 list 中，每個元素都是一個完整的 Python 物件，具備了各自的類別與資訊，因此在計算同質資料時，需要透過 for 迴圈迭代，將裡面的物件一一取出來進行運算。

而 Numpy 的 ndarray 則具備了同質資料型態的特性，也就是在 ndarray 裡**每一個元素都必須有相同的資料型態**，因此在計算時，ndarray 的效能和語法相較內建的 list 更快速簡潔。

## 二、 Ndarray 的創建

在 Numpy 裡，ndarray 是由 array 物件組成。在匯入 Numpy 之後，我們可以使用兩種方式來創建數值陣列。第一種方式是使用 Numpy 裡的 array() 方法將 list 轉換成 ndarray，第二種方式是使用 Numpy 的多樣化函式來創建 ndarray。

### **1. 將 list 轉換成 ndarray**

- **np.array()**

    我們可以使用 np.array() 將單層的 list 轉換成一維的數值陣列：

    ```python
    list_1=[0, 1, 2, 3, 4, 5]
    data = np.array(list_1)
    print(data)
    print(type(data))
    print(data.dtype)
    ```

    ```python
    # 輸出：
    [1 2 3 4 5]               #  data 陣列的值
    <class 'numpy.ndarray'>   #  data 陣列的型別
    int64                     #  data 陣列內物件的型別
    ```
    []()

    np.array() 也可以將兩層 list 轉換成二維的數值陣列：

    ```python
    list_2=[[0, 1, 2, 3, 4], [5, 6, 7, 8, 9]]
    data = np.array(list_2)
    print(data)
    print(type(data))
    print(data.dtype)
    ```

    ```python
    # 輸出：
    [[0 1 2 3 4]              #  data 陣列的值
     [5 6 7 8 9]]
    <class 'numpy.ndarray'>   #  data 陣列的型別
    int64                     #  data 陣列內物件的型別
    ```

    > 使用 print('\n') 列印空白列，也就是進行換行的動作

### 2. 使用 Numpy 的多樣化函式來創建 ndarray
Numpy 中，也提供許多的方法來讓我們快速建立陣列，在 import numpy as np 後，即可以藉由「 np.方法名稱」來使用 Numpy 所提供的各種方法。

- **np.zeros()**

    可以使用 np.zeros() 快速建立所有元素為 0 的陣列，比如創建所有元素為 0，長度為 5，型別為 int 的一維數值陣列：

    ```python
    # np.zeros()
    print(np.zeros(5,dtype=int))
    ```

    ```python
    # 輸出：
    [0 0 0 0 0]
    ```

- **np.ones()**

    也可以使用 np.ones() 快速建立所有元素為 1 的陣列，比如創建所有元素為 1 ，長度為 2x5，型別為 float 的二維數值陣列：

    ```python
    # np.ones()
    print(np.ones((2, 5),dtype=float)) 
    ```

    ```python
    # 輸出：
    [[1. 1. 1. 1. 1.]
     [1. 1. 1. 1. 1.]]
    ```

- **np.full()：**

    除了 0 和 1 之外，我們還可以建立所有元素為指定值的陣列，比如創建所有元素指定為 2，長度為 3x2x5，型別為 int 的三維數值陣列：

    ```python
    # np.full()
    print(np.full((3, 2, 5), 2))
    ```

    ```python
    # 輸出：
    [[[2 2 2 2 2]
      [2 2 2 2 2]]

     [[2 2 2 2 2]
      [2 2 2 2 2]]

     [[2 2 2 2 2]
      [2 2 2 2 2]]]
    ```

- **np.random.random()**

    或是建立所有元素為 0 到 1 之間隨機數值的陣列，比如建立元素為 0 到 1 之間的隨機數值，長度為 3x4 的二維數值陣列：

    ```python
    # np.random.random()
    print(np.random.random((3, 4)))
    ```

    ```python
    # 輸出：
    [[0.78837773 0.78191722 0.38002785 0.17772392]
     [0.94851325 0.08781078 0.00229052 0.63474405]
     [0.51463031 0.91391908 0.1534682  0.88046589]]
    ```

- **np.ramdom.randint()**

    除了浮點數之外，也可以建立所有元素為指定範圍間隨機整數的陣列，比如建立所有元素為 0 到 10 之間的隨機整數，長度為 3x4 的二維數值陣列：

    ```python
    # np.ramdom.randint()
    print(np.random.randint(0, 10, (3, 4)))
    ```

    ```python
    # 輸出：
    [[9 7 1 5]
     [5 3 8 2]
     [9 2 9 2]]
    ```

- **np.arange()**

    若要建立指定範圍的連續整數陣列，常常也會使用 np.arange()的方法，比如創建從 0 到 11 的連續整數陣列：

    ```python
    # np.arange()
    print(np.arange(12))
    ```

    ```python
    # 輸出：
    [ 0  1  2  3  4  5  6  7  8  9 10 11]

    ```

    另外，可以透過 reshape() 函式重新組合陣列，比如 3x4 二維數值陣列：

    ```python
    # 組合長度為 3x4 的二維陣列
    print(np.arange(12).reshape(3, 4))
    ```

    ```python
    # 輸出：
    [[ 0  1  2  3]
     [ 4  5  6  7]
     [ 8  9 10 11]]
    ```

    > 以句點區隔來查詢物件的狀態、執行物件具有的功能(如函式、方法、屬性)，是物件導向程式設計的特徵。

## 三、維度與元素數量

在 Numpy 中我們可以透過 ndim 屬性及 size 屬性來取得陣列的維度與元素數量，藉由這些屬性，我們就可以得知資料的大小：

```python
data = np.random.randint(0, 10, (3, 4))
print(data)
print('\n')
print('維度:',data.ndim)
print('形狀:',data.shape)
print('元素數量:',data.size)
```

```python
# 輸出：
[[8 7 8 5]
 [8 3 3 9]
 [3 0 1 4]]

維度: 2
形狀: (3, 4)
元素數量: 12
```


## 四、不同維度的陣列

如同上方的例子，我們可以依照不同需求來創建一維陣列、二維陣列，甚至是多維度的陣列，而根據不同維度的陣列，也擁有各自的名稱，分別為**純量、向量、矩陣、張量**。

### 1. 純量 (Scalar)
純量是指沒有維度的數值：

```python
scalar = np.array(1234)
print(scalar)
print('維度:',scalar.ndim)
print('形狀:',scalar.shape)
```

```python
# 輸出：
1234
維度:0
形狀:()
```

### 2. 向量 (Vector)
向量指具有一個維度的數值陣列：

```python
vector = np.array([1, 2, 3, 4])
print(vector)
print('維度:',vector.ndim)
print('形狀:',vector.shape)
```

```python
# 輸出：
[1 2 3 4]
維度:1
形狀:(4,)
```

### 3. 矩陣 (Matrix)
矩陣是指具有兩個維度的數值陣列：

```python
matrix = np.array([1, 2, 3, 4]).reshape(2, 2)
print(matrix)
print('維度:',matrix.ndim)
print('形狀:',matrix.shape)
```

```python
# 輸出：
[[1 2]
    [3 4]]
維度:2
形狀:(2, 2)
```

### 4. 張量 (Tensor)
張量指三個維度以及超過三個維度的數值陣列：

```python
tensor = np.array([1, 2, 3, 4]*3).reshape(3, 2, 2)
print(tensor)
print('維度:',tensor.ndim)
print('形狀:',tensor.shape)
```

```python
# 輸出：
[[[1 2]
    [3 4]]

    [[1 2]
    [3 4]]

    [[1 2]
    [3 4]]]
維度:3
形狀:(3, 2, 2)
```



## 六、亂數種子

所謂的亂數是指不具規則性的隨機數值，在資料分析時，多用於將收集的資料進行隨機分離或加上隨機值使資料不一致。

而亂數在每次執行得到的結果可能都不相同，但在進行資料分析時，經常需要在之後進行驗證，為了確保結果的一致，我們可以設定亂數種子，使每次亂數執行的結果不會改變。

對於該隨機數值的初始值即稱為種子，我們可以使用 np 的 random.seed() 進行種子的設定：

```python
# 種子設定
np.random.seed(0)

# 產生常態分佈(平均為0標準差為1)的 10 個亂數
print(np.random.randn(10))
```

```python
# 輸出：
[ 1.76405235  0.40015721  0.97873798  2.2408932   1.86755799 -0.97727788
  0.95008842 -0.15135721 -0.10321885  0.4105985 ]
```

> Python 本身也提供亂數的功能，但在資料分析中通常使用 Numpy 的亂數功能。


[]()
[]()


Nupmpy 還提供許多非常好用的方法和功能，想了解和學習更多的話，可以參考官方文件： [Numpy Documentation](https://numpy.org/) ㄛ!