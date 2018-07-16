# Longest Common Prefix
## 题目：
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:

Input: ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
Note:

All given inputs are in lowercase letters a-z.
## 分析：
只要找出前面相同的最多的，那么遍历就可以了。
## 代码
```C
char* longestCommonPrefix(char** strs, int strsSize) {
    char* temp;
    int i,j;           
    if(strsSize<=0) return "";
    temp=strs[0];
    for(i=1;i<strsSize;i++){ 
        j=0;
        while(temp[j]&&strs[i][j]&&temp[j]==strs[i][j]) j++;
        temp[j]='\0';
    }
    return temp;
}
