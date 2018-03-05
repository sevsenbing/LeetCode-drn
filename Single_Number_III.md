# Single Number III
## 题目：
Given an array of numbers nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once.

For example:

Given nums = [1, 2, 1, 3, 2, 5], return [3, 5].

Note:
The order of the result is not important. So in the above example, [5, 3] is also correct.
Your algorithm should run in linear runtime complexity. Could you implement it using only constant space complexity?
Credits:
Special thanks to @jianchao.li.fighter for adding this problem and creating all test cases.

## 分析：
这道题与single number I相似，唯一不同的地方是这里有两个single number。因此可以将数组拆成两组。<br>
nums里有两个不同数的话，计算nums的异或运算取得的值一定是两个single number的异或运算的值。<br>
取得的值（比如c）,c的二进制数中，第一个1，肯定为single numbers同一位上不同的值，利用这点，设置出一个值，再次与nums进行按位与运算，就可以分成两组了，每组的异或运算的值就是不同的single numbers。<br>

## 代码：
```ruby
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* singleNumber(int* nums, int numsSize, int* returnSize) {
    int i=0,res=0,bit=1;
    for(i=0;i<numsSize;i++){
        res^=nums[i];
    }
    while((res&1)==0){
        bit <<= 1;
        res >>= 1;
    }
    *returnSize = 2;
    int*dog=(int*)malloc(sizeof(int)*2);
    dog[0]=0;
    dog[1]=0;
    for(i=0;i<numsSize;i++){ 
        if((nums[i]&bit)==0) dog[0]^=nums[i];
        else dog[1]^=nums[i];
    }
    return dog;
}
```

## 收获：
中间学了几个关键知识点。<br>
&：按位与 如果两个相应的二进制位都为1，则该位的结果值为1，否则为0 <br>
|：按位或 两个相应的二进制位中只要有一个为1，该位的结果值为1  <br>
^：按位异或 若参加运算的两个二进制位值相同则为0，否则为1  <br>
~：取反 ~是一元运算符，用来对一个二进制数按位取反，即将0变1，将1变0  <br>
<<：左移 用来将一个数的各二进制位全部左移N位，右补0  <br>
>>：右移  将一个数的各二进制位右移N位，移到右端的低位被舍弃，对于无符号数，高位补0 <br>
