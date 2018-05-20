# Base 7
## 题目：
Given an integer, return its base 7 string representation.

Example 1:
Input: 100
Output: "202"
Example 2:
Input: -7
Output: "-10"
Note: The input will be in range of [-1e7, 1e7].

## 分析：
将十进制的数变为七进制。需要注意的判断是正负。<br>

## 代码：
```ruby
class Solution {
public:
    string convertToBase7(int num) {
        if(num==0) return "0";
        string ans="";
        bool f=num>0;
        while(num!=0){
            ans=to_string(abs(num%7))+ans;
            num/=7;
        }
        return f?ans:"-"+ans;
    }
};
