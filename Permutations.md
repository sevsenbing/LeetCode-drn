# Permutations
## 题目：
Given a collection of distinct integers, return all possible permutations.

Example:

Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
## 分析：
题中要求输出给定数组的所有排列可能。<br>
可以额外定义一个函数去遍历所有可能。<br>
如果要遍历的话就得写一个flag标记被遍历过的。<br>
## 代码：
```ruby
class Solution {
public:  
    vector<vector<int> >ans;   
    int shu[10],flag[10]; 
    vector<vector<int> > permute(vector<int>&num){  
        ans.clear();  
        memset(flag,0,sizeof(flag)); 
        int n=num.size();  
        bl(n,0,num);  
        return ans;  
    }  
    void bl(int n,int m,vector<int> &num){  
        if(m==n){  
            vector<int>t;  
            for(int i=0;i<n;i++)t.push_back(num[shu[i]]);  
            ans.push_back(t);  
            return;  
        }  
        for(int i=0;i<n;i++){  
            if(flag[i]==0){  
                flag[i]=1;  
                shu[m]=i;  
                bl(n,m+1,num);  
                flag[i]=0;  
            }  
        }  
    }  
};  
