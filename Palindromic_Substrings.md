# Palindromic Substrings
***
## 题目：
Given a string, your task is to count how many palindromic substrings in this string.

The substrings with different start indexes or end indexes are counted as different substrings even they consist of same characters.
```
Example 1:
Input: "abc"
Output: 3
Explanation: Three palindromic strings: "a", "b", "c".
```
```
Example 2:
Input: "aaa"
Output: 6
Explanation: Six palindromic strings: "a", "a", "a", "aa", "aa", "aaa".
```
Note:
The input string length won't exceed 1000.
## 分析：
这道题让数出回文的全部个数，那就设两个字符串，其中一个是正的，另一个是反着的，然后看相不相等。
## 代码：
```ruby
class Solution {
public:
    int countSubstrings(string s) {
        string s1="",s2 = "";
        int ans=0;
        for(int i=0;i<s.size();i++){
            for(int j=1;j+i<=s.size();j++){
                s1=s.substr(i, j);s2=s1;
                reverse(s1.begin(),s1.end());
                if(s2==s1) ans++;
                s1="";s2="";
            }
        }
        return ans;
    }
};
