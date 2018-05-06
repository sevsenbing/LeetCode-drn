# Perfect Number
## 题目：
We define the Perfect Number is a positive integer that is equal to the sum of all its positive divisors except itself.

Now, given an integer n, write a function that returns true when it is a perfect number and false when it is not.
Example:
Input: 28
Output: True
Explanation: 28 = 1 + 2 + 4 + 7 + 14
Note: The input number n will not exceed 100,000,000. (1e8)
## 分析
这道题要求判断除自身以外的因子相加是否能等于数本身。<br>
首先1肯定不是了<br>
其次注意遍历的时候起点设的位置。<br>
## 代码：
```ruby
class Solution {
public:
    bool checkPerfectNumber(int num) {
        if(num==1) return false;
        int sum=1;
        for(int i=2;i*i<=num;i++){
            if(num%i==0) sum+=(i+num/i);
            if(i*i==num) sum-=1;
            if(sum>num)return false;
        }
        return num==sum;
    }
};
