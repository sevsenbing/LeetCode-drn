# 1.Array Partition
## 题目
Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

Example 1:
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).
Note:
n is a positive integer, which is in the range of [1, 10000].
All the integers in the array will be in the range of [-10000, 10000].

## 分析
只需要排序再累加即可。<br>

## 代码：
```ruby
class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
        int ans=0,n=nums.size();
        sort(nums.begin(),nums.end());
        for(int i=0;i<n;i+=2) ans+=nums[i];
        return ans;
    }
};
```

# 2.Assigh Cookies
## 题目
Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie. Each child i has a greed factor gi, which is the minimum size of a cookie that the child will be content with; and each cookie j has a size sj. If sj >= gi, we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.

Note:
You may assume the greed factor is always positive. 
You cannot assign more than one cookie to one child.

Example 1:
Input: [1,2,3], [1,1]

Output: 1

Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3. 
And even though you have 2 cookies, since their size is both 1, you could only make the child whose greed factor is 1 content.
You need to output 1.
Example 2:
Input: [1,2], [1,2,3]

Output: 2

Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
You have 3 cookies and their sizes are big enough to gratify all of the children, 
You need to output 2.

## 分析
输出的是饼干数量可以满足几个小朋友，因此只要遍历和判断结合就可以啦。<br>

## 代码
```ruby
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        sort(s.begin(),s.end());
        sort(g.begin(),g.end());
        int ans=0;
        for(int i=0;i<s.size();i++){
            if(ans>=g.size()) break;
            if(s[i]>=g[ans]) ans++;
        }
        return ans;
    }
};
```



