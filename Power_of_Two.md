# Power of Two
***
## 题目：
Given an integer, write a function to determine if it is a power of two.
## 分析：

首先1肯定可以被2整除，这个要特别说明<br>
不停地除二就行了！大概是最好想的递归。<br>

## 代码：
```ruby
class Solution {
public:
    bool isPowerOfTwo(int n) {
    if(n==1)   return true;  
    if(n>=2 && n%2==0)   return isPowerOfTwo(n/2);  
    return false;     
    }
};
```
## 法二：

二的整除，其实想到了二进制。要知道能被二整除的数都是只有一个1剩下都是0<br>
用这个规律进行判断<br>

## 法二的代码：
```ruby
class Solution {
public:
    bool isPowerOfTwo(int n) {
        int ans=0;
        while(n>0){
            ans+=(n&1);
            n>>=1;
        }
        return cnt==1;
    }
};
```
## 又是一行就能解决的代码。
它的二进数最高位为1，其它都为0。<br>
如果减1，最高位降一位，0的位变为1<br>
两数相与，得到0<br>
```ruby
class Solution {
public:
    bool isPowerOfTwo(int n) {
        return n > 0 && ((n & (n - 1)) == 0 );  
    }
};
```
