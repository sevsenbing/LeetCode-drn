# Add Binary
## 题目：
Given two binary strings, return their sum (also a binary string).

For example,
a = "11"
b = "1"
Return "100".

## 分析：

就是从后往前加，然后看有没有进位什么的<br>

## 代码:
```ruby
class Solution {
public:
    string addBinary(string a, string b) {
        string ans;
        int la=a.length(),lb=b.length(),lmax=max(la,lb),add='0';
        if(la==0) return b;
        if(lb == 0) return a;
        for (int i=0;i<lmax;i++){
            char ca=la>i?a[la-i-1]:'0';
            char cb=lb>i?b[lb-i-1]:'0';
            char s=(ca==cb?'0':'1');
            char sj=(s==add?'0':'1');
            if(ca=='1'&&cb=='1'||s=='1'&&add=='1')add = '1';
            else add = '0';
            ans+=sj;
        }
        if(add=='1') ans+=add;
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
