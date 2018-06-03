# Combination Sum IV
## 题目：
Given an integer array with all positive numbers and no duplicates, find the number of possible combinations that add up to a positive integer target.
```
Example:

nums = [1, 2, 3]
target = 4

The possible combination ways are:
(1, 1, 1, 1)
(1, 1, 2)
(1, 2, 1)
(1, 3)
(2, 1, 1)
(2, 2)
(3, 1)
```
Note that different sequences are counted as different combinations.

Therefore the output is 7.
Follow up:
What if negative numbers are allowed in the given array?
How does it change the problem?
What limitation we need to add to the question to allow negative numbers?
## 分析：
这道题给出一个数组，一个目标数，让求出数组里的数有多少种方法相加得目标数。<br>
这道题我第一感觉就是用动态规划做，算是一个比较复杂的爬梯子的题。<br>
就是设一个数组，比如ans[i]=a，意思就是有a种方法相加得a，然后后面的数再和前面的组合就ok。<br>
## 代码
```C++
class Solution {
public:
    int combinationSum4(vector<int>& nums, int target) {
        vector<int> ans(target+1);
        ans[0]=1;
        for(int i=1;i<=target;i++) {
            for(int j:nums){
                if(i>=j) ans[i]+=ans[i-j];
            }
        }
        return ans[target];
    }
};
