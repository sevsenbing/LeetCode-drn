# Count Binary Substrings
## 题目：
Give a string s, count the number of non-empty (contiguous) substrings that have the same number of 0's and 1's, and all the 0's and all the 1's in these substrings are grouped consecutively.

Substrings that occur multiple times are counted the number of times they occur.

Example 1:
Input: "00110011"
Output: 6
Explanation: There are 6 substrings that have equal number of consecutive 1's and 0's: "0011", "01", "1100", "10", "0011", and "01".

Notice that some of these substrings repeat and are counted the number of times they occur.

Also, "00110011" is not a valid substring because all the 0's (and 1's) are not grouped together.
Example 2:
Input: "10101"
Output: 4
Explanation: There are 4 substrings: "10", "01", "10", "01" that have equal number of consecutive 1's and 0's.
Note:

s.length will be between 1 and 50,000.
s will only consist of "0" or "1" characters.

## 分析：

设置m,n来标记<br>
m,n分别代表当前数字，和前一个数字。<br>
如果m和n相等，就计算次数。<br>
否则就更新次数。<br>
接着通过判断统计子数组的个数，如果这时该数字之前的数字连续次数n大于等于当前数字连续次数m，则令子数组个数ans加1。<br>

## 代码：
```ruby
class Solution {
public:
    int countBinarySubstrings(string s) {
        int n=0,m=1,ans=0;
        for (int i=1;i<s.size();i++){
            if(s[i]==s[i-1]) cur++;
            else{
                n=m;
                m=1;
            }
            if(n>=cur) ans++;
        }
        return ans;
    }
};
