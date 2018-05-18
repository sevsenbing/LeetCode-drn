# Basic Calculator II
## 问题：
Implement a basic calculator to evaluate a simple expression string.

The expression string contains only non-negative integers, +, -, *, / operators and empty spaces . The integer division should truncate toward zero.

Example 1:

Input: "3+2*2"
Output: 7
Example 2:

Input: " 3/2 "
Output: 1
Example 3:

Input: " 3+5 / 2 "
Output: 5
Note:

You may assume that the given expression is always valid.
Do not use the eval built-in library function.
## 分析：
注意处理数字和符号。以及f的初始化，我一开始没有给F初始化。导致wa了好几次才找到哪里错了。<br>
## 代码：
```ruby
class Solution {
public:
    int calculate(string s) {
        int ans= 0,ll=0,num=0;
        char f='+';
        for(int i=0;i<s.size();i++){
            char fh=s[i];
            if(fh>=48&&fh<=57) num=num*10+fh-48;
            if(fh=='+'||fh=='-'||fh=='*'||fh=='/'||i==s.size()-1){
                switch(f){
                    case'+': ll+=num; break;
                    case'-': ll-=num; break;
                    case'*': ll*=num; break;
                    case'/': ll/=num; break;
                } 
                if(fh=='+'||fh=='-'||i==s.size()-1){
                    ans+=ll;ll=0;
                }
                f=fh;num=0;
            } 
        }
        return ans;
    }
};
