# Reverse String
## 题目：
Write a function that takes a string as input and returns the string reversed.

Example:
Given s = "hello", return "olleh".
## 分析：
遍历就好<br>
## 代码：
```ruby
class Solution {
public:
    string reverseString(string s) {
        string ans;  
        int l=s.size(),i=0,j=s.size()-1;  
        if(s.size()==0) return ans;
        while(i<s.size()){
            ans+=s[j];  
            i++;  
            j--;  
        }  
        return ans;
    }
};
