# Relative Ranks
## 题目：
Given scores of N athletes, find their relative ranks and the people with the top three highest scores, who will be awarded medals: "Gold Medal", "Silver Medal" and "Bronze Medal".

Example 1:
Input: [5, 4, 3, 2, 1]
Output: ["Gold Medal", "Silver Medal", "Bronze Medal", "4", "5"]
Explanation: The first three athletes got the top three highest scores, so they got "Gold Medal", "Silver Medal" and "Bronze Medal". 
For the left two athletes, you just need to output their relative ranks according to their scores.
Note:
N is a positive integer and won't exceed 10,000.
All the scores of athletes are guaranteed to be unique.

## 分析：
我们可以建立一个优先队列，把分数和坐标放进去，然后就会自动排序。<br>
从顶端开始一个一个取出数据，由于保存了其在原数组的位置。<br>
直接将存到结果ans中正确位置，用一个变量记录。<br>

## 代码：
```ruby
class Solution {
public:
    vector<string> findRelativeRanks(vector<int>& nums) {
        int x=1,n=nums.size();
        vector<string> ans(n,"");
        priority_queue<pair<int,int>>q;
        for(int i=0;i<n;i++) q.push({nums[i],i});
        for(int i=0;i<n;i++){
            int y=q.top().second;q.pop();
            if(x==1) ans[y]="Gold Medal";
            else if(x==2) ans[y]="Silver Medal";
            else if(x==3) ans[y]="Bronze Medal";
            else ans[y]=to_string(x);
            x++;
        }
        return ans;
    }
};
