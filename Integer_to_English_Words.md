# Integer to English Words
***
## 题目：
Convert a non-negative integer to its english words representation. Given input is guaranteed to be less than 231 - 1.
```
Example 1:

Input: 123
Output: "One Hundred Twenty Three"
```
```
Example 2:

Input: 12345
Output: "Twelve Thousand Three Hundred Forty Five"
```
```
Example 3:

Input: 1234567
Output: "One Million Two Hundred Thirty Four Thousand Five Hundred Sixty Seven"
```
### 分析
这道题要把数字形式的数转化成单词形式。<br>
因为这道题是英文题，所以有必要找一下英文十进制计数的特点，也就是三个一组，但是前一千又比较特殊。前一千中前二十又特殊，因此额外定义一个函数方便操作。<br>
### 代码
```ruby
class Solution {
public:
    string numberToWords(int num) {
        string ans=convertHundred(num%1000);
        vector<string> v={"Thousand","Million","Billion"};
        for (int i=0;i<3;i++){
            num/=1000;
            ans=num%1000?convertHundred(num%1000)+" "+v[i]+" "+ans:ans;
        }
        while(ans.back()==' ') ans.pop_back();
        return ans.empty()?"Zero":ans;
    }
    string convertHundred(int num){
        vector<string> ts={"", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine", "Ten", "Eleven", "Twelve", "Thirteen", "Fourteen", "Fifteen", "Sixteen", "Seventeen", "Eighteen", "Nineteen"};
        vector<string> pt={"", "", "Twenty", "Thirty", "Forty", "Fifty", "Sixty", "Seventy", "Eighty", "Ninety"};
        string ans;
        int a=num/100,b=num%100,c=num%10;
        ans=b<20?ts[b]:pt[b/10]+(c?" "+ts[c]:"");
        if(a>0) ans=ts[a]+" Hundred"+(b?" "+ans:"");
        return ans;
    }
};
