# Repeated String Match
## 题目：
Given two strings A and B, find the minimum number of times A has to be repeated such that B is a substring of it. If no such solution, return -1.

For example, with A = "abcd" and B = "cdabcdab".

Return 3, because by repeating A three times (“abcdabcdabcd”), B is a substring of it; and B is not a substring of A repeated two times ("abcdabcd").

Note:
The length of A and B will be between 1 and 10000.
## 分析：
要用B来匹配A，则A需要重复几次。<br>
遍历a和b中字符，比较a和b的每个字符。<br>
用(i+j)%m在a中取字符，j小于从而避免越界，如果匹配，j++。<br>
循环结束后，如果j=n，说明成功匹配。<br>
通过(i+j-1)/m + 1计算a的重复次数。<br>
当i+j正好等于m时，说明不用重复，那么(i+j-1)/m + 1还是等于1，当i+j>m的时候，需要重复。<br>
## 代码：
```ruby
class Solution {
public:
    int repeatedStringMatch(string A, string B) {
        int m=A.size(),n=B.size();
        for (int i=0;i<m;++i){
            int j=0;
            while(j<n&&A[(i+j)%m]==B[j])++j;
            if(j==n) return(i+j-1)/m+1;
        }
        return -1;
    }
};
