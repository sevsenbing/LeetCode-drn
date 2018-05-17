# Decode Ways
## 题目：
A message containing letters from A-Z is being encoded to numbers using the following mapping:

'A' -> 1
'B' -> 2
...
'Z' -> 26
Given a non-empty string containing only digits, determine the total number of ways to decode it.

Example 1:

Input: "12"
Output: 2
Explanation: It could be decoded as "AB" (1 2) or "L" (12).
Example 2:

Input: "226"
Output: 3
Explanation: It could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).
## 分析：
采用动态分布的做法，但是由于是26个字母需要判断一些地方。比如二位数的话如果是十几那么个位数可以是一到九，如果二十几那么个位数只能到6.<br>
## 代码
```ruby
class Solution {
public:
    int numDecodings(string s) {
        vector<int>ans(s.size()+1,0);
        ans[0]=1;
        for(int i=1;i<s.size()+1;i++){
            ans[i]=(s[i-1]=='0')?0:ans[i-1];
            if(i>1&&(s[i-2]=='1'||(s[i-2]=='2'&&s[i-1]<='6'))) ans[i]+=ans[i-2];
        }
        return ans.back();
    }
};
