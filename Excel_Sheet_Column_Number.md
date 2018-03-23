# Excel Sheet Column Number
## 题目：
Related to question Excel Sheet Column Title

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
Credits:
Special thanks to @ts for adding this problem and creating all test cases.
## 分析：
这道题的思路是26进制。
## 代码：
```ruby
class Solution {
public:
    int titleToNumber(string s) {
        int he=0,shu=0;  
        for (int i=0;i<s.length();++i){  
            shu=s[i]-'A'+1;  
            he=26*he+shu;  
        }  
        return he;  
    }
};
