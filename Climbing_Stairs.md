# Climbing Stairs
***
## 题目：
You are climbing a stair case. It takes n steps to reach to the top.<br>

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?<br>

Note: Given n will be a positive integer.<br>

Example 1:
```
Input: 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```
Example 2:
```
Input: 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```
## 分析：
动态规划的方法。<br>
## 代码：
```C++
class Solution {
public:
    int climbStairs(int n) {
        if(n<=1) return 1;
        vector<int>m(n);
        m[0]=1; m[1]=2;
        for(int i=2;i<n;i++) m[i]=m[i-1]+m[i-2];
        return m.back();
    }
};
