# Delete and Earn
## 题目：
Given an array nums of integers, you can perform operations on the array.

In each operation, you pick any nums[i] and delete it to earn nums[i] points. After, you must delete every element equal to nums[i] - 1 or nums[i] + 1.

You start with 0 points. Return the maximum number of points you can earn by applying such operations.

Example 1:
Input: nums = [3, 4, 2]
Output: 6
Explanation: 
Delete 4 to earn 4 points, consequently 3 is also deleted.
Then, delete 2 to earn 2 points. 6 total points are earned.
Example 2:
Input: nums = [2, 2, 3, 3, 3, 4]
Output: 9
Explanation: 
Delete 3 to earn 3 points, deleting both 2's and the 4.
Then, delete 3 again to earn 3 points, and 3 again to earn 3 points.
9 total points are earned.
Note:

The length of nums is at most 20000.
Each element nums[i] is an integer in the range [1, 10000].

## 分析：
这道题的意思是在一个数组中选取一个数字，选完之后计入积分，但是该数字+1—1的数字同时会被移除并且不计入积分。<br>
那么这道题就是一个抉择问题了.判断要不要删除这个数字，还要看这个数字之前之后。<br>

## 代码：
```ruby
class Solution {
public:
    int deleteAndEarn(vector<int>& nums) {
        vector<int> h(10001, 0);
        int n=0,bn=0;
        for (int i=0;i<nums.size();i++) h[i]+=i;
        for (int i=0;i<10001;i++){
            int nq=bn+h[i];
            int bnq=n>bn?n:bn;
            n=nq; 
            bn=bnq;
        }
        return n>bn?n:bn;
    }
};
