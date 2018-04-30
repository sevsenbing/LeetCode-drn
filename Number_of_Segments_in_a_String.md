# Number of Segments in a String
## 题目：
Count the number of segments in a string, where a segment is defined to be a contiguous sequence of non-space characters.

Please note that the string does not contain any non-printable characters.

Example:

Input: "Hello, my name is John"
Output: 5
## 分析
题很简单找空格就行。
## 代码：
```ruby
class Solution {
public:
    int countSegments(string s) {
        int ans=0;
        for (int i=0;i<s.size();i++) {
            if(s[i]==' ') continue;
            ++ans;
            while(i<s.size()&&s[i]!=' ') ++i;
        }
        return ans;
    }
};
