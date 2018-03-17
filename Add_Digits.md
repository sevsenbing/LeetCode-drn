# Add Digits
## 题目
Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

For example:

Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.

Follow up:
Could you do it without any loop/recursion in O(1) runtime?

Credits:
Special thanks to @jianchao.li.fighter for adding this problem and creating all test cases.
## 循环的代码：
```rudy
class Solution {
public:
    int addDigits(int num) {
        int a=0,b=0;
        while(num>9){
            a=num%10;
            b=num/10;
            num=a+b;
        }
        return num;
    }
};
```
## 分析：
这道题有一个fallow up,说是不用循环或者递归，就可以解决。那么，根据列举找规律<br>
1 1    10 1    19 1    ……<br>
2 2    11 2    20 2    ……<br>
3 3    12 3    21 3<br>
4 4    13 4    22 4<br>
5 5    14 5    23 5<br>
6 6    15 6    24 6<br>
7 7    16 7    25 7<br>
8 8    17 8    26 8<br>
9 9    18 9    27 9<br>
规律已经很明显了，每九个数字一个循环。<br>
## 不循环的代码：
```ruby
class Solution {
public:
    int addDigits(int num) {
        int a;
        a=num%9;
        if(num>0&&a==0) a=9;
        return a;
    }
};
```

看了有一种写法，只用输出一行代码，并且避免0和9的问题，强无敌。
```ruby
class Solution {
public:
    int addDigits(int num) {
        return (num-1)%9+1;
    }
};
