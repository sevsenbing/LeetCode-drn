# Largest Number
## 问题：
Given a list of non negative integers, arrange them such that they form the largest number.

Example 1:

Input: [10,2]
Output: "210"
Example 2:

Input: [3,30,34,5,9]
Output: "9534330"
Note: The result may be very large, so you need to return a string instead of an integer.

## 分析
因为要组成最大数字，但是有十位数也有个位数。想组成最大数就得知道各个数字有多长，可以把数字转换成字符型。<br>
但是转成字符型的话，用sort排序就不好使了，这时候就需要重新写一个规则方便sort排序。<br>
## 代码：
```ruby
class Solution {
public:
    static bool px(string a,string b){return a+b>b+a;}
    string largestNumber(vector<int> &num){
        vector<string> s;
        for(int i=0;i<num.size();i++) s.push_back(to_string(num[i]));  
        sort(s.begin(),s.end(),px);
        string ans="";
        for(int i=0;i<s.size();i++) ans+=s[i]; 
        if(ans[0]=='0') return "0";
        return ans;
    }
};
