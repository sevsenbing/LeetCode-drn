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
这道题的意思是给出两个字符看这两个字符串是否是相同的，在给出字符串中，“*”可以表示前一个字符的相同字符的任意个数，“.“表示任何字符。<br>
这道题
这道题的意思是给出两个字符看这两个字符串是否是相同的，在给出字符串中，“*”可以表示前一个字符的相同字符的任意个数，“.“表示任何字符。的
这道题的意思是给出两个字符看这两个字符串是否是相同的，在给出字符串中，“*”可以表示前一个字符的相同字符的任意个数，“.“表示任何字符。
