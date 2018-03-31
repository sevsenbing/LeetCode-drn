# Binary Watch
## 题目：
A binary watch has 4 LEDs on the top which represent the hours (0-11), and the 6 LEDs on the bottom represent the minutes (0-59).
Each LED represents a zero or one, with the least significant bit on the right.
【图:二进制表】
For example, the above binary watch reads "3:25".

Given a non-negative integer n which represents the number of LEDs that are currently on, return all possible times the watch could represent.

Example:

Input: n = 1
Return: ["1:00", "2:00", "4:00", "8:00", "0:01", "0:02", "0:04", "0:08", "0:16", "0:32"]
Note:
The order of output does not matter.
The hour must not contain a leading zero, for example "01:00" is not valid, it should be "1:00".
The minute must be consist of two digits and may contain a leading zero, for example "10:2" is not valid, it should be "10:02".
## 分析：
利用bitset的类，可将任意进制数转为二进制。<br>
运用。那么时针从0遍历到11，分针从0遍历到59，然后我们把时针的数组左移6位加上分针的数值，然后统计1的个数，即为亮灯的个数，我们遍历所有的情况，当其等于num的时候，存入结果res中，
利用bitset的类，可将任意进制数转为二进制。<br>而且又用到了count函数，用来统计1的个数construction。那么时针从0遍历到11，分针从0遍历到59，然后我们把时针的数组左移6位加上分针的数值，然后统计1的个数，即为亮灯的个数，我们遍历所有的情况，当其等于num的时候，存入结果res中，
利用bitset的类，可将任意进制数转为二进制。<br>而且又用到了count函数，用来统计1的个数。那么时针从0遍历到11，分针从0遍历到59，然后我们把时针的数组左移6位加上分针的数值，然后统计1的个数，即为亮灯的个数，我们遍历所有的情况，当其等于num的时候，存入结果res中，
## 题目：
```ruby
class Solution {
public:
    vector<string> readBinaryWatch(int num) {
        vector<string>ans;
        for (int i=0;i<12;i++)
            for (int j=0;j<60;j++)
                if(bitset<10>((i<<6)+j).count()==num) ans.push_back(to_string(i)+(j<10?":0":":")+to_string(j));
        return ans;
    }
};
