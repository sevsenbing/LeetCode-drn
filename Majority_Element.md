# Majority Element
## 题目：
Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

You may assume that the array is non-empty and the majority element always exist in the array.
```
Example 1:

Input: [3,2,3]
Output: 3
Example 2:

Input: [2,2,1,1,1,2,2]
Output: 2
```
## 分析：
运用计数器。
## 代码
```C++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int ans=0,m=0;
        for(int n:nums){
            if(m==0){
                ans=n;
                m++;
            }
            else (n==ans)?m++:m--;
        }
        return ans;
    }
};
