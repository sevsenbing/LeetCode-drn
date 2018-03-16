# 2 Keys Keyboard
## 题目：
Initially on a notepad only one character 'A' is present. You can perform two operations on this notepad for each step:

Copy All: You can copy all the characters present on the notepad (partial copy is not allowed).
Paste: You can paste the characters which are copied last time.
Given a number n. You have to get exactly n 'A' on the notepad by performing the minimum number of steps permitted. Output the minimum number of steps to get n 'A'.

Example 1:
Input: 3
Output: 3
Explanation:
Intitally, we have one character 'A'.
In step 1, we use Copy All operation.
In step 2, we use Paste operation to get 'AA'.
In step 3, we use Paste operation to get 'AAA'.
Note:
The n will be in the range [1, 1000].

## 分析：
这道题题意是根据复制黏贴完成给出的复制次数，通过列举可以发现，复制和粘贴的总步数不会高于数字本身。<br>
但是，举个例子，如果给出的数字是6，最少的情况是五步，因为6可以222也可以33。<br>
可以看出能让数字步数缩小的原因，即出现n%i==0。<br>

## 代码：
```ruby
class Solution {
public:
    int minSteps(int n) {
        int ans=0;
        for(int i=2;i<=n;i++){
            while(n%i==0){
                ans+=i;
                n/=i;
            }
        }
        return ans;
    }
}; 
