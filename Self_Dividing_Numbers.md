# Self Dividing Numbers
## 题目：
A self-dividing number is a number that is divisible by every digit it contains.

For example, 128 is a self-dividing number because 128 % 1 == 0, 128 % 2 == 0, and 128 % 8 == 0.

Also, a self-dividing number is not allowed to contain the digit zero.

Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible.

Example 1:
Input: 
left = 1, right = 22
Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]
Note:

The boundaries of each input argument are 1 <= left <= right <= 10000.
## 分析：
额外定义函数用来判断能不能自除，并且需要注意被除数不能是0。<br>
## 代码：
```ruby
class Solution {
public:
    bool is(int num){
        int temp=num,d=0;
        while(1){
            d=temp%10;
            if(d==0||num%d!=0) return false;
            temp/=10;
        }
        return true;
    }
    vector<int> selfDividingNumbers(int left, int right) {
        vector<int> ans;
        for(int i=left;i<=right;i++){
            if(is(i)) ans.push_back(i);
        }
        return ans;
    }
};
