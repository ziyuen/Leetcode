## Method 1

```cpp
// A school method based C++ program to  
// check if a number is prime 
#include <bits/stdc++.h> 
using namespace std; 
  
// function check whether a number  
// is prime or not 
bool isPrime(int n) 
{ 
    // Corner case 
    if (n <= 1) 
        return false; 
  
    // Check from 2 to n-1 
    for (int i = 2; i < n; i++) 
        if (n % i == 0) 
            return false; 
  
    return true; 
} 
  
// Driver Program 
int main() 
{ 
    isPrime(11) ? cout << " true\n" :  
                  cout << " false\n"; 
    return 0; 
} 
```

## Method 2 : 

判断 k 是否能被 2~√k 间的整数除，
因为大于 √n 能整除 k 的数肯定是之前 2~√n 的数的倍数


```cpp
int isPrime(int k) {
    for (int j = 2; j <= sqrt(k); j++) {
        if(k % j == 0)    // 如果不为素0 
           return 0;
    }
    return 1;    // 反之则返回1 
}
```

方法二明显复杂度更小