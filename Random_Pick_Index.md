# Random Pick Index
## 题目：
Given an array of integers with possible duplicates, randomly output the index of a given target number. You can assume that the given target number must exist in the array.

Note:
The array size can be very large. Solution that uses too much extra space will not pass the judge.

Example:

int[] nums = new int[] {1,2,3,3,3};
Solution solution = new Solution(nums);

// pick(3) should return either index 2, 3, or 4 randomly. Each index should have equal probability of returning.
solution.pick(3);

// pick(1) should return 0. Since in the array only nums[0] is equal to 1.
solution.pick(1);
## 分析：
注意遇到目标的处理,遍历数组，如果不是目标就跳过，如果是就加一。然后随机生成数字，若是0，则为i<br>
## 代码：
```ruby
class Solution {
private:
    vector<int> v;
public:
    Solution(vector<int> nums):v(nums) {}
    int pick(int target){
        int cnt=0,res=-1;
        for (int i=0;i<v.size();i++){
            if(v[i]!=target) continue;
            ++cnt;
            if(rand()%cnt==0) res=i;
        }
        return res;
    }
};

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * int param_1 = obj.pick(target);
 */
