# Subarray Sum Equals K
## 题目：
Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.

Example 1:
Input:nums = [1,1,1], k = 2
Output: 2
Note:
The length of the array is in range [1, 20,000].
The range of numbers in the array is [-1000, 1000] and the range of the integer k is [-1e7, 1e7].

## 分析：
这道题大概意思是在给定的数组中找出连续的分数组，数组中的数相加等于目标值，最后返回此类数组的个数。我的做法就是利用两个for循环。</br>
不过我这个方法运行了288ms，应该是最烂的方法，上网看了一下别人的做法都是用哈希表。

## 代码：
```ruby
int subarraySum(int* nums, int numsSize, int k) {
    int res=0;
    for(int i=0;i<numsSize;i++){
        int sum=nums[i];
        if(sum==k) res++;
        for(int j=i+1;j<numsSize;j++){
            sum=sum+nums[j];
            if(sum==k) res++;
        }
    }
    return res;
}
