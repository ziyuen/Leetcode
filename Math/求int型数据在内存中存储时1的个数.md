```
int main() {
    int num;
    while(cin >> num) {
        int count = 0;
        while(num > 0) {
            if(num%2)count += 1;
            num /= 2;
        }
        cout << count << endl;
    }
    return 0;
}
```
1. 输入一个整数（int类型）
2. 这个数转换成2进制后，输出1的个数

输入 5，输出 2