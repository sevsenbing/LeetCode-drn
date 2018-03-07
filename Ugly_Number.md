# Ugly Number
## 题目：
Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

Note that 1 is typically treated as an ugly number.

Credits:
Special thanks to @jianchao.li.fighter for adding this problem and creating all test cases.

## 分析：
直接while循环，如果模2、3、5等于零就除去，再继续。<br>
注意特殊情况，0，负数什么的。<br>

## 代码：
```ruby
bool isUgly(int num) {
    if(num<=0) return false;
    while(num>=2){
        if(num%2==0) num/=2;
        else if(num%3==0) num/=3;
        else if(num%5==0) num/=5;
        else return false;
    }
    return num=1 ;
}
