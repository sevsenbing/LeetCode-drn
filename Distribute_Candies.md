# Distribute Candies
## 题目：
Given an integer array with even length, where different numbers in this array represent different kinds of candies. Each number means one candy of the corresponding kind. You need to distribute these candies equally in number to brother and sister. Return the maximum number of kinds of candies the sister could gain.
Example 1:
Input: candies = [1,1,2,2,3,3]
Output: 3
Explanation:
There are three different kinds of candies (1, 2 and 3), and two candies for each kind.
Optimal distribution: The sister has candies [1,2,3] and the brother has candies [1,2,3], too. 
The sister has three different kinds of candies. 
Example 2:
Input: candies = [1,1,2,3]
Output: 2
Explanation: For example, the sister has candies [2,3] and the brother has candies [1,1]. 
The sister has two different kinds of candies, the brother has only one kind of candies. 
Note:

The length of the given array is in range [2, 10,000], and will be even.
The number in given array is in range [-100,000, 100,000].

## 分析：

## 代码：
```ruby
class Solution {
public:
    int distributeCandies(vector<int>& candies) {
        sort(candies.begin(),candies.end());
          int ans=0,last=-1,o=0,size=candies.size();
          for(int i=0;i<size;i++){
              if(last!=candies[i]){
                  last=candies[i];
                  ans++;
                 o++;
             }
             else o--;
         }
         return o>0?ans-o/2:ans;
    }
}
}
