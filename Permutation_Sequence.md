# Permutation Sequence
***
## 题目：
The set [1,2,3,...,n] contains a total of n! unique permutations.<br>

By listing and labeling all of the permutations in order, we get the following sequence for n = 3:<br>

"123"<br>
"132"<br>
"213"<br>
"231"<br>
"312"<br>
"321"<nr>
Given n and k, return the kth permutation sequence.<nr>

Note:<br>

Given n will be between 1 and 9 inclusive.<br>
Given k will be between 1 and n! inclusive.<br>
## 分析：
通过找规律有：
```
an-1 = kn-2 / 1!
kn-1 = kn-2 / 1!
an = kn-1 / 0!
kn = kn-1 % 0!
```
## 代码：
```C++
class Solution {
public:
    string getPermutation(int n, int k) {
        string ans;
        string num="123456789";
        vector<int> f(n,1);
        for (int i=1;i<n;i++) f[i]=f[i-1]*i;
        k--;
        for(int i=n;i>=1;i--){
            int j=k/f[i-1];
            k%=f[i-1];
            ans.push_back(num[j]);
            num.erase(j,1);
        }
        return ans;
    }
};
