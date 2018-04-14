# Valid Anagram
## 题目：
Given two strings s and t, write a function to determine if t is an anagram of s.

For example,
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.

Note:
You may assume the string contains only lowercase alphabets.

Follow up:
What if the inputs contain unicode characters? How would you adapt your solution to such case?

## 分析：
继续处理寒假的历史遗留问题……这道题我大概当时没有理解题意吧<br>
其实很简单的一道题，只要排序再比教就行了。

## 代码：
```ruby
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.empty()&&t.empty()) return true;
        else if(s.empty()||t.empty()) return false;
        sort(s.begin(), s.end());
        sort(t.begin(), t.end());
        if(s==t) return true;
        return false;       
    }
};
