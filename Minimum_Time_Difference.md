# Minimum Time Difference
## 题目：
Given a list of 24-hour clock time points in "Hour:Minutes" format, find the minimum minutes difference between any two time points in the list.
Example 1:
Input: ["23:59","00:00"]
Output: 1
Note:
The number of time points in the given list is at least 2 and won't exceed 20000.
The input time is legal and ranges from 00:00 to 23:59.
## 分析：
非常简单的思路，先排序，再计算，注意小时和分钟要分开。<br>
## 代码
```ruby
class Solution {
public:
    int findMinDifference(vector<string>& timePoints) {
        int ans=INT_MAX,d;
        sort(timePoints.begin(),timePoints.end());
        for(int i=0;i<timePoints.size();i++){
            string t=timePoints[i],tt=timePoints[(i+1)%timePoints.size()];
            d=((tt[0]-48)*10+(tt[1]-48)-(t[0]-48)*10-(t[1]-48))*60+(tt[3]-48)*10+(tt[4]-48)-(t[3]-48)*10-(t[4]-48);
            if(i==timePoints.size()-1) d+=24*60;
            ans=min(ans,d);
        }
        return ans;
    }
};
