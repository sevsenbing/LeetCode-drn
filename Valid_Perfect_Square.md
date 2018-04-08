# Valid Perfect Square
## 题目：
Given a positive integer num, write a function which returns True if num is a perfect square else False.

Note: Do not use any built-in library function such as sqrt.

Example 1:

Input: 16
Returns: True
Example 2:

Input: 14
Returns: False
## 分析：
### 就是遍历，有一个问题就是我一开始的遍历条件是(int i=0;i*i<=num;i++)居然超时了。到现在都想不明白。<br>
## 代码
```ruby
class Solution {
public:
    bool isPerfectSquare(int num) {
        for(int i=1;i<=num/i;i++){
            if(i*i==num) return true;
        }
        return false;
    }
};
```
### 另一个方法就是运用平方的规律做。
```ruby
class Solution {
public:
    bool isPerfectSquare(int num) {
        int i=1;
        while(num>0){
            num-=i;
            i+=2;
        }
        return num==0;
    }
};
