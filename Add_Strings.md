# Add Strings
## 题目
Given two non-negative integers num1 and num2 represented as string, return the sum of num1 and num2.

Note:

The length of both num1 and num2 is < 5100.
Both num1 and num2 contains only digits 0-9.
Both num1 and num2 does not contain any leading zero.
You must not use any built-in BigInteger library or convert the inputs to integer directly.
## 分析
各位相加，最后根据进位情况看需不需要补高位。
## 代码
```ruby
class Solution {
public:
    string addStrings(string num1, string num2) {
        string ans="";
        int a=num1.size(),b=num2.size(),i=a-1,j=b-1,gao=0;
        while(i>= 0||j >=0){
            int m=(i>=0?num1[i--]-'0':0);
            int n=(j>=0?num2[j--]-'0':0);
            int sum=m+n+gao;
            ans.insert(ans.begin(),sum%10+'0');
            gao=sum/10;
        }
        return (gao?"1"+ans:ans);
    }
};
