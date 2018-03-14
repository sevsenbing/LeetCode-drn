# 1-bit and 2-bit Characters
## 题目
We have two special characters. The first character can be represented by one bit 0. The second character can be represented by two bits (10 or 11).

Now given a string represented by several bits. Return whether the last character must be a one-bit character or not. The given string will always end with a zero.

Example 1:
Input: 
bits = [1, 0, 0]
Output: True
Explanation: 
The only way to decode it is two-bit character and one-bit character. So the last character is one-bit character.
Example 2:
Input: 
bits = [1, 1, 1, 0]
Output: False
Explanation: 
The only way to decode it is two-bit character and two-bit character. So the last character is NOT one-bit character.
Note:

1 <= len(bits) <= 1000.
bits[i] is always 0 or 1.
## 分析：
这题是判断最后一个0是0还是10，因此只要遍历数组，遇到1就+2，遇到0就++<br>
## 代码
```ruby
bool isOneBitCharacter(int* bits, int bitsSize) {
    int i=0;
    while(i<bitsSize-1){
        if(bits[i]==1) i+=2;
        else i++;
    }
    return (i==bitsSize-1?true:false);
}
