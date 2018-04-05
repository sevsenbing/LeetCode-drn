# Count and Say
## 题目：
The count-and-say sequence is the sequence of integers with the first five terms as following:

1.     1
2.     11
3.     21
4.     1211
5.     111221
1 is read off as "one 1" or 11.
11 is read off as "two 1s" or 21.
21 is read off as "one 2, then one 1" or 1211.
Given an integer n, generate the nth term of the count-and-say sequence.

Note: Each term of the sequence of integers will be represented as a string.

Example 1:

Input: 1
Output: "1"
Example 2:

Input: 4
Output: "1211"

## 分析：
解决了一下历史遗留问题，这道题是我假期被折磨到半夜一点也没做出来只好换别的题的可怕存在。<br>
不过今天又看了一下觉得还挺简单的<br>
答题思路就是，相同的数字计数，然后放到下一个字符串里。字符串最爽的一点就是字符可以相加。<br>

## 代码：
```ruby
class Solution {
public:
    string countAndSay(int n) {
        string ans="1";
        for(int i=1;i<n;i++){
            string temp="";
            for(int j=0,count;j<ans.size();j++){
                 for(count=1;j<ans.size()&&ans[j]==ans[j+1];j++) count++;
                 temp=temp+(char)(count+48)+ans[j];
             }
             ans=temp;
         }
         return ans;
    }
};
