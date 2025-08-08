<h2><a href="https://leetcode.com/problems/spiral-matrix">54. Spiral Matrix</a></h2><h3>Medium</h3><hr><p>Given an <code>m x n</code> <code>matrix</code>, return <em>all elements of the</em> <code>matrix</code> <em>in spiral order</em>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/spiral1.jpg" style="width: 242px; height: 242px;" />
<pre>
<strong>Input:</strong> matrix = [[1,2,3],[4,5,6],[7,8,9]]
<strong>Output:</strong> [1,2,3,6,9,8,7,4,5]
</pre>

<p><strong class="example">Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/spiral.jpg" style="width: 322px; height: 242px;" />
<pre>
<strong>Input:</strong> matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
<strong>Output:</strong> [1,2,3,4,8,12,11,10,9,5,6,7]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == matrix.length</code></li>
	<li><code>n == matrix[i].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 10</code></li>
	<li><code>-100 &lt;= matrix[i][j] &lt;= 100</code></li>
</ul>

## Solution
### C++
```c++
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        int n = matrix.size(), m = matrix[0].size();
        int r1 = 0, r2 = n - 1, c1 = 0, c2 = m - 1;
        vector<int> ans;

        while(r1 <= r2 && c1 <= c2) {
            for(int i = c1; i<=c2; i++) {
                ans.push_back(matrix[r1][i]);
            }
            r1++;
            if(r1 > r2) break;

            for(int i = r1; i<=r2; i++) {
                ans.push_back(matrix[i][c2]);
            }
            c2--;
            if(c1 > c2) break;

            for(int i = c2; i>=c1; i--) {
                ans.push_back(matrix[r2][i]);
            }
            r2--;
            if(r1 > r2) break;

            for(int i = r2; i>=r1; i--) {
                ans.push_back(matrix[i][c1]);
            }
            c1++;
            if(c1 > c2) break;
        }

        return ans;
    }
};
```

### Java
```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        int n = matrix.length, m = matrix[0].length;
        int r1 = 0, r2 = n - 1, c1 = 0, c2 = m - 1;
        List<Integer> ans = new ArrayList<>();

        while(r1 <= r2 && c1 <= c2) {
            for(int i = c1; i<=c2; i++) {
                ans.add(matrix[r1][i]);
            }
            r1++;
            if(r1 > r2) break;

            for(int i = r1; i<=r2; i++) {
                ans.add(matrix[i][c2]);
            }
            c2--;
            if(c1 > c2) break;

            for(int i = c2; i>=c1; i--) {
                ans.add(matrix[r2][i]);
            }
            r2--;
            if(r1 > r2) break;

            for(int i = r2; i>=r1; i--) {
                ans.add(matrix[i][c1]);
            }
            c1++;
            if(c1 > c2) break;
        }

        return ans;
    }
}
```