# Lexicographical Numbers
## 问题：
Given an integer n, return 1 - n in lexicographical order.

For example, given 13, return: [1,10,11,12,13,2,3,4,5,6,7,8,9].

Please optimize your algorithm to use less time and space. The input size may be as large as 5,000,000.

## 分析：
很简单，遍历就可以。注意处理不同数字开头的交界处。<br>
## 代码：
```ruby
class Solution {
public:
    vector<int> lexicalOrder(int n) {
        vector<int> ans(n);
        int m=1;
        for(int i=0;i<n;i++){
            ans[i]=m;
            if(m*10<=n) m*=10;
            else{
                if(m>=n) m/=10;
                m+=1;
                while(m%10==0) m/=10;
            }
        }
        return ans;
    }
};
