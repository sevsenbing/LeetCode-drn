# Power of Three && four
## 题目：
Given an integer (signed 32 bits), write a function to check whether it is a power of 3（4）.

## 分析：
和昨天做的powerof2思路差不多<br>
## 代码：
3：
```ruby
class Solution {
public:
    bool isPowerOfFour(int num) {
        while(num&&num%3==0) num/=3;
        return num==1;
    }
};
```
4：
```ruby
class Solution {
public:
    bool isPowerOfFour(int num) {
        while(num&&num%4==0) num/=4;
        return num==1;
    }
};
```
## 一行代码的解法：
3的可以有取巧的做法就是用小于INT_MAX的最大的3的数除以判断的数就可以啦<br>
``` ruby
class Solution {
public:
    bool isPowerOfThree(int n) {
        return (n>0&&1162261467%n==0);
    }
};
```
这样的话昨天power of 2有了新做法。<br>
```ruby
class Solution {
public:
    bool isPowerOfTwo(int n) {
    return (n>0&&2147483648%n==0);    
    }
};
```
不过最奇怪的地方就是只能用数字，不能用INT_MAX！奇怪！<br>
