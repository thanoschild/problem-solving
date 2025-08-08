<h2><a href="https://leetcode.com/problems/word-search/">79. Word Search</a></h2><h3>Medium</h3><hr><div><p>Given an <code>m x n</code> grid of characters <code>board</code> and a string <code>word</code>, return <code>true</code> <em>if</em> <code>word</code> <em>exists in the grid</em>.</p>

<p>The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/04/word2.jpg" style="width: 322px; height: 242px;">
<pre><strong>Input:</strong> board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCCED"
<strong>Output:</strong> true
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/04/word-1.jpg" style="width: 322px; height: 242px;">
<pre><strong>Input:</strong> board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "SEE"
<strong>Output:</strong> true
</pre>

<p><strong class="example">Example 3:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/15/word3.jpg" style="width: 322px; height: 242px;">
<pre><strong>Input:</strong> board = [["A","B","C","E"],["S","F","C","S"],["A","D","E","E"]], word = "ABCB"
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == board.length</code></li>
	<li><code>n = board[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 6</code></li>
	<li><code>1 &lt;= word.length &lt;= 15</code></li>
	<li><code>board</code> and <code>word</code> consists of only lowercase and uppercase English letters.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong> Could you use search pruning to make your solution faster with a larger <code>board</code>?</p>
</div>

## Solution
### C++
```c++
class Solution {
public:
    int dir[5] = {-1, 0, 1, 0, -1};

    bool dfs(vector<vector<char>>& board, string word, int i, int j, int k, int n, int m) {
        if(k == word.size()) return true;
        if(i < 0 || i >= n || j < 0 || j >= m || board[i][j] != word[k]) return false;

        board[i][j] = '*';
        bool flag = false;

        for(int d = 0; d<4; d++) {
            flag = flag || dfs(board, word, i + dir[d], j + dir[d+1], k+1, n, m);
        }

        board[i][j] = word[k];
        return flag;
    }

    bool exist(vector<vector<char>>& board, string word) {
        int n = board.size(), m = board[0].size();

        for(int i = 0; i<n; i++) {
            for(int j = 0; j<m; j++) {
                if(board[i][j] == word[0] && dfs(board, word, i, j, 0, n, m)) return true;
            }
        }

        return false;
    }
};
```

### Java
```java
class Solution {
    int dir[] = {-1, 0, 1, 0, -1};

    private boolean dfs(char[][] board, String word, int i, int j, int k, int n, int m) {
        if(k == word.length()) return true;
        if(i < 0 || i >= n || j < 0 || j >= m || board[i][j] != word.charAt(k)) return false;

        board[i][j] = '*';
        boolean flag = false;

        for(int d = 0; d<4; d++) {
            flag = flag || dfs(board, word, i + dir[d], j + dir[d+1], k+1, n, m);
        }

        board[i][j] = word.charAt(k);
        return flag;
    }

    public boolean exist(char[][] board, String word) {
        int n = board.length, m = board[0].length;

        for(int i = 0; i<n; i++) {
            for(int j = 0; j<m; j++) {
                if(board[i][j] == word.charAt(0) && dfs(board, word, i, j, 0, n, m)) return true;
            }
        }

        return false;
    }
}
```