#  Count of Smaller Numbers After Self
## 题目：
You are given an integer array nums and you have to return a new counts array. The counts array has the property where counts[i] is the number of smaller elements to the right of nums[i].

Example:

Given nums = [5, 2, 6, 1]

To the right of 5 there are 2 smaller elements (2 and 1).
To the right of 2 there is only 1 smaller element (1).
To the right of 6 there is 1 smaller element (1).
To the right of 1 there is 0 smaller element.
Return the array [2, 1, 1, 0].

## 分析：
一开始用的最普通的for循环，果然超时了。<br>
如果用二分法插入一个新数组，新数组会有序，那么新加入数组在有序数组对应的数字，就是结果。<br>
insert:表示插入元素。<br>

## 代码：
```ruby
class Solution {
public:
    vector<int> countSmaller(vector<int>& nums){
        vector<int>t,res(nums.size());
        for (int i=nums.size()-1;i>=0;--i){
            int l=0,r=t.size();
            while (l<r){
                int m=l+(r-l)/2;
                if (t[m]>=nums[i]) r=m;
                else l=m+1;
            }
            res[i]=r;
            t.insert(t.begin()+r,nums[i]);
        }
        return res;
    }
};
