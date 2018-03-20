# Battleships in a Board
## 题目：
Given an 2D board, count how many battleships are in it. The battleships are represented with 'X's, empty slots are represented with '.'s. You may assume the following rules:
You receive a valid board, made of only battleships or empty slots.
Battleships can only be placed horizontally or vertically. In other words, they can only be made of the shape 1xN (1 row, N columns) or Nx1 (N rows, 1 column), where N can be of any size.
At least one horizontal or vertical cell separates between two battleships - there are no adjacent battleships.
Example:
X..X
...X
...X
In the above board there are 2 battleships.
Invalid Example:
...X
XXXX
...X
This is an invalid board that you will not receive - as battleships will always have a cell separating between them.
Follow up:
Could you do it in one-pass, using only O(1) extra memory and without modifying the value of the board?

## 分析：
这题大概意思是给出一组只有.和X的二维数组，一串直的X代表船，.表示没有船<br>
从而求出一共有几条船<br>
那么只需要遍历二维数组即可，因为X是直的才说明是个船。所以如果左边或者上边有X就不用结果加一了<br>

## 代码：
```ruby
class Solution {
public:
    int countBattleships(vector<vector<char>>& board) {
        int ans=0;
        for(int i=0;i<board.size();++i){
            for(int j=0;j<board[0].size();++j){
                if(board[i][j]=='.'||(i>0&&board[i-1][j]=='X')||(j>0&&board[i][j-1]=='X')) continue;
                ans++;
            }
        }
        return ans;
    }
};
