# Excel Sheet Column Title
## 题目：
Given a positive integer, return its corresponding column title as appear in an Excel sheet.<br>

For example:
```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
    ...
```
```
Example 1:

Input: 1
Output: "A"

Example 2:

Input: 28
Output: "AB"

Example 3:

Input: 701
Output: "ZY"
```
## 分析：
当做二十六进制即可，注意开头是一。
## 代码:
```C++
class Solution {
public:
    string convertToTitle(int n) {
        string ans="";
        while(n){
            ans=(char)((n-1)%26+'A')+ans;
            n=(n-1)/26;
        }
        return ans;
    }
};
