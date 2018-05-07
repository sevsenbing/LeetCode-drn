# Regular Expression Matching
## 题目：
Given an input string (s) and a pattern (p), implement regular expression matching with support for '.' and '*'.

'.' Matches any single character.
'*' Matches zero or more of the preceding element.
The matching should cover the entire input string (not partial).

Note:

s could be empty and contains only lowercase letters a-z.
p could be empty and contains only lowercase letters a-z, and characters like . or *.
Example 1:

Input:
s = "aa"
p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
Example 2:

Input:
s = "aa"
p = "a*"
Output: true
Explanation: '*' means zero or more of the precedeng element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".
Example 3:

Input:
s = "ab"
p = ".*"
Output: true
Explanation: ".*" means "zero or more (*) of any character (.)".
Example 4:

Input:
s = "aab"
p = "c*a*b"
Output: true
Explanation: c can be repeated 0 times, a can be repeated 1 time. Therefore it matches "aab".
Example 5:

Input:
s = "mississippi"
p = "mis*is*p*."
Output: false
## 分析：
这道题的意思是给出两个字符看这两个字符串是否是相同的，在给出字符串中星号可以表示前一个字符的任意个数，而”.“表示任何字符.<br>
这道题的难点在于情况比较多。<br>
如果，给出字符串是空的，若都为空返回true，反之false。<br>
如果，给出的只有一个字符，若相等或为”.“返回true，其余false。<br>
如果，p的第二个字符不是星号，s为空，返回false，否则判断首字符是否匹配，且从第二个字符开始调用递归。<br>
如果，p的第二个字符为星号，s不为空，字符匹配，调用递归，若匹配，返回true，否则s去掉首字母。<br>
返回调用递归函数匹配s和去掉前两个字符的p。<br>
## 代码：
```ruby
class Solution {
public:
    bool isMatch(string s, string p) {
        if(p.empty()) return s.empty();
        if(p.size()==1) return (s.size()==1&&(s[0]==p[0]||p[0]=='.'));
        if(p[1]!='*'){
            if(s.empty()) return false;
            return (s[0]==p[0]||p[0]=='.')&&isMatch(s.substr(1),p.substr(1));
        }
        while(!s.empty()&&(s[0]==p[0]||p[0]=='.')){
            if(isMatch(s,p.substr(2))) return true;
            s=s.substr(1);
        }
        return isMatch(s,p.substr(2));
    }
};
