# Multiply Strings
## 题目：
Given two non-negative integers num1 and num2 represented as strings, return the product of num1 and num2, also represented as a string.
```
Example 1:

Input: num1 = "2", num2 = "3"
Output: "6"
```
```
Example 2:

Input: num1 = "123", num2 = "456"
Output: "56088"
```
Note:<br>
<br>
The length of both num1 and num2 is < 110.<br>
Both num1 and num2 contain only digits 0-9.<br>
Both num1 and num2 do not contain any leading zero, except the number 0 itself.<br>
You must not use any built-in BigInteger library or convert the inputs to integer directly.<br>

## 分析：
每位相乘，错位相加，然后存放到数组里，注意数组的容量，
## 代码：
```C++
class Solution {
public:
    string multiply(string num1, string num2) {
        string ans;
        int n1=num1.size(),n2=num2.size();
        int k=n1+n2-2,n=0;
        vector<int> v(n1+n2,0);
        for(int i=0;i<n1;i++){
            for(int j=0;j<n2;j++)
                v[k-i-j]+=(num1[i]-'0')*(num2[j]-'0');
        }
        for(int i=0;i<n1+n2;i++){
            v[i]+=n;
            carry=v[i]/10;
            v[i]%=10;
        }
        int i=n1+n2-1;
        while(v[i]==0) i--;
        if(i<0) return "0";
        while(i>=0) ans.push_back(v[i--]+'0');
        return ans;
    }
};
