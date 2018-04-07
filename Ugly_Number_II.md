# Ugly Number II
## 题目：
Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.

Note that 1 is typically treated as an ugly number, and n does not exceed 1690.

## 分析：
#### 这道题和丑数一很想，这个是可以被2 3 5整除的数就是丑数。并且1就是丑数<br>
#### 接下来就是把已经求得的数组中的某个元素乘上2或者3或者5得到下一个应该存入数组的丑数。<br>
#### 丑数的下标初始化时下标都为0，加入新数后2 3 5要乘的数相应后移。<br>

## 代码：
```ruby
class Solution {
public:
    int nthUglyNumber(int n) {
        vector<int> ans(n);
        int i_2=0,i_3=0,i_5=0,v_2=2,v_3=3,v_5=5,i=1;
        ans[0]=1;
        for(;i<n;i++){
            int v=min(v_2,min(v_3,v_5));
            if(v==v_2){
                ans[i]=v_2;
                i_2++;
                v_2=ans[i_2]*2;
            }
            if(v==v_3){
                ans[i]=v_3;
                i_3++;
                v_3=ans[i_3]*3;
            }
            if(v==v_5){
                ans[i]=v_5;
                i_5++;
                v_5=ans[i_5]*5;
            }
        }
        return ans[n - 1];
    }
};
