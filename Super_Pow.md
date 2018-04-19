# Super Pow
## 题目：
Your task is to calculate ab mod 1337 where a is a positive integer and b is an extremely 
large positive integer given in the form of an array.

Example1:

a = 2
b = [3]

Result: 8
Example2:

a = 2
b = [1,0]

Result: 1024
## 分析：
这道题求一个数的平方对1337取余。<br>
设了一个额外的函数方便运算<br>

## 代码：
```ruby
class Solution {
public:
    int pow(int x, int n) {
        if(n==0) return 1;
        if(n==1) return x%1337;
        return pow(x%1337,n/2)*pow(x%1337,n-n/2)%1337;
    }
    int superPow(int a, vector<int>& b) {
        long ans=1;
        for(int i=0;i<b.size();i++) ans=pow(ans,10)*pow(a,b[i])%1337;
        return ans;
    }
};
