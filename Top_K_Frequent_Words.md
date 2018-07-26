# Top K Frequent Words
******
## 题目：
***
```
Given a non-empty list of words, return the k most frequent elements.

Your answer should be sorted by frequency from highest to lowest. If two words have the same frequency, then the word with the lower alphabetical order comes first.

Example 1:
Input: ["i", "love", "leetcode", "i", "love", "coding"], k = 2
Output: ["i", "love"]
Explanation: "i" and "love" are the two most frequent words.
    Note that "i" comes before "love" due to a lower alphabetical order.
Example 2:
Input: ["the", "day", "is", "sunny", "the", "the", "the", "sunny", "is", "is"], k = 4
Output: ["the", "is", "sunny", "day"]
Explanation: "the", "is", "sunny" and "day" are the four most frequent words,
    with the number of occurrence being 4, 3, 2 and 1 respectively.
Note:
You may assume k is always valid, 1 ≤ k ≤ number of unique elements.
Input words contain only lowercase letters.
Follow up:
Try to solve it in O(n log k) time and O(n) extra space.
```
***
## 分析：
***
根据字母出现次数建立多组，单词按字符顺序进行排序。利用set的自动排序的功能，使其能按字母顺序排列。map是从小到大排序的，倒序遍历所有组取pair，次数最大。
***
## 代码：
***
```C++
class Solution {
public:
    vector<string> topKFrequent(vector<string>& words, int k) {
        vector<string> ans;
        unordered_map<string, int> freq;
        vector<set<string>> v(words.size()+1, set<string>());
        for(string word : words) freq[word]++;
        for(auto a : freq) v[a.second].insert(a.first);
        for (int i=v.size()-1;i>=0;i--){
            if(k<=0) break;
            vector<string> t(v[i].begin(),v[i].end());
            if(k>=t.size()) ans.insert(ans.end(),t.begin(),t.end());
            else ans.insert(ans.end(),t.begin(),t.begin()+k);
            k-=t.size();
        }
        return ans;
    }
};
