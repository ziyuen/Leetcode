qsort的难点在于怎么写compare function

The qsort() function in C++ sorts a given array in ascending order using Quicksort algorithm.

qsort() Parameters
base: Pointer to the first element of the array to sort
num: Number of element in the array
size: Size in bytes of each element in the array
compare: A pointer to a function that that compares two elements. 
1. It returns a negative integer if the first argument is less than the second
2. a positive integer if the first argument is greater than the second
3. zero if both arguments are equal

首先qsort是将数组升序排序的，
当左边元素小于右边元素时，cmp函数返回一个负数
当左边元素大于右边元素时，cmp函数返回一个正数
相等则返回 0

换言之，想要第一个元素在左，第二个元素在右，可以让cmp函数返回一个负值
反之，想要第一个元素在右，第二个元素在左，可以让cmp函数返回一个正值

利用这个规则可以自定义 cmp函数

例题见 Sort/179.Largest number