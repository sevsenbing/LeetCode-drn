# Longest Harmonious Subsequence
## 题目：
```
We define a harmonious array is an array where the difference between its maximum value and its minimum value is exactly 1.

Now, given an integer array, you need to find the length of its longest harmonious subsequence among all its possible subsequences.

Example 1:
Input: [1,3,2,2,5,2,3,7]
Output: 5
Explanation: The longest harmonious subsequence is [3,2,2,2,3].
Note: The length of the input array will not exceed 20,000.

```
## 分析：
利用map的自动排序的特性，遍历map的时候就是从小往大开始遍历，
从第二个映射对开始遍历，每次跟其前面的映射对比较，如果二者的数字刚好差1，那么就把二个数字的出现的次数相加并更新结果
## 代码：
```C++
class Solution {
public:
    int findLHS(vector<int>& nums) {
        if (nums.empty()) return 0;
        int res = 0;
        map<int, int> m;
        for (int num : nums) ++m[num];
        for (auto it = next(m.begin()); it != m.end(); ++it) {
            auto pre = prev(it);
            if (it->first == pre->first + 1) {
                res = max(res, it->second + pre->second);
            }
        }
        return res;
    }
};
