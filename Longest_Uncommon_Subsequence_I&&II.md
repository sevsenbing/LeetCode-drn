#  Longest Uncommon Subsequence I
## 题目：
Given a group of two strings, you need to find the longest uncommon subsequence of this group of two strings. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings.

A subsequence is a sequence that can be derived from one sequence by deleting some characters without changing the order of the remaining elements. Trivially, any string is a subsequence of itself and an empty string is a subsequence of any string.

The input will be two strings, and the output needs to be the length of the longest uncommon subsequence. If the longest uncommon subsequence doesn't exist, return -1.

Example 1:
Input: "aba", "cdc"
Output: 3
Explanation: The longest uncommon subsequence is "aba" (or "cdc"), 
because "aba" is a subsequence of "aba", 
but not a subsequence of any other strings in the group of two strings. 
Note:

Both strings' lengths will not exceed 100.
Only letters from a ~ z will appear in input strings.
## 分析：
其实主要是做II，I就是两字符串相等就返回-1，否则返回较长的。改了改自己a的代码变成一行<br>
## 代码：
```ruby
class Solution {
public:
    int findLUSlength(string a, string b) {
        return a==b?-1:max(a.size(),b.size());
    }
};

# Longest Uncommon Subsequence II
## 题目：
Given a list of strings, you need to find the longest uncommon subsequence among them. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be any subsequence of the other strings.

A subsequence is a sequence that can be derived from one sequence by deleting some characters without changing the order of the remaining elements. Trivially, any string is a subsequence of itself and an empty string is a subsequence of any string.

The input will be a list of strings, and the output needs to be the length of the longest uncommon subsequence. If the longest uncommon subsequence doesn't exist, return -1.

Example 1:
Input: "aba", "cdc", "eae"
Output: 3
Note:

All the given strings' lengths will not exceed 10.
The length of the given list will be in the range of [2, 50].
## 分析：
遍历所有字符串再判断<br>
## 代码：
```ruby
class Solution {
public:
    int findLUSlength(vector<string>& strs) {
        int ans=-1,j=0,n=strs.size();
        for(int i=0;i<n;i++){
            for(j=0;j<n;j++){
                if(j==i) continue;
                if(panduan(strs[i],strs[j])) break;
            }
            if(j==n) ans=max(ans,(int)strs[i].size());
        }
        return ans;
    }
    int panduan(string str1,string str2){
        int i=0;
        for(char m:str2){
            if(m==str1[i]) i++;
            if(i==str1.size()) break;
        }
        return i==str1.size();
    }
};
