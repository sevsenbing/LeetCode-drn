# Longest Repeating Character Replacement
***
## 题目：
Given a string that consists of only uppercase English letters, you can replace any letter in the string with another letter at most k times. Find the length of a longest substring containing all repeating letters you can get after performing the above operations.

Note:
Both the string's length and k will not exceed 104.
```
Example 1:

Input:
s = "ABAB", k = 2

Output:
4

Explanation:
Replace the two 'A's with two 'B's or vice versa.
```
```
Example 2:

Input:
s = "AABABBA", k = 1

Output:
4
```
Explanation:
Replace the one 'A' in the middle with 'B' and form "AABBBBA".
The substring "BBBB" has the longest repeating letters, which is 4.
## 分析：
这道题让找出最长重复的字符串,设一个st，初始化为0遍历字符串，设一个ji累加出现字符的个数，出现最多字符的个数是max。
a=字符串的总长度减去出现次数最多的字符的个数。满足啊<=k即可。
## 代码：
```C++
class Solution {
public:
    int characterReplacement(string s, int k) {
        int ans=0,Max=0,st=0;
        vector<int>ji(26,0);
        for (int i=0;i<s.size();i++){
            Max=max(Max,++ji[s[i]-'A']);
            while (i-st+1-Max>k){
                ji[s[st]-'A']--;st++;
            }
            ans=max(ans,i-st+1);
        }
        return ans;
    }
};
