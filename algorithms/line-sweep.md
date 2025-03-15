<h2><a href="https://leetcode.com/problems/zero-array-transformation-i">3639. Zero Array Transformation I</a></h2><h3>Medium</h3><hr><p>You are given an integer array <code>nums</code> of length <code>n</code> and a 2D array <code>queries</code>, where <code>queries[i] = [l<sub>i</sub>, r<sub>i</sub>]</code>.</p>

<p>For each <code>queries[i]</code>:</p>

<ul>
	<li>Select a <span data-keyword="subset">subset</span> of indices within the range <code>[l<sub>i</sub>, r<sub>i</sub>]</code> in <code>nums</code>.</li>
	<li>Decrement the values at the selected indices by 1.</li>
</ul>

<p>A <strong>Zero Array</strong> is an array where all elements are equal to 0.</p>

<p>Return <code>true</code> if it is <em>possible</em> to transform <code>nums</code> into a <strong>Zero Array </strong>after processing all the queries sequentially, otherwise return <code>false</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [1,0,1], queries = [[0,2]]
<strong>Output:</strong> true
<strong>Explanation:</strong> 
<li><strong>For i = 0:</strong>
Select the subset of indices as <code>[0, 2]</code> and decrement the values at these indices by 1.
The array will become <code>[0, 0, 0]</code>, which is a Zero Array.
</pre>


<p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [4,3,2,1], queries = [[1,3],[0,2]]
<strong>Output:</strong> false
<strong>Explanation:</strong> 
<li><strong>For i = 0:</strong>
Select the subset of indices as <code>[1, 2, 3]</code> and decrement the values at these indices by 1.
The array will become <code>[4, 2, 1, 0]</code>.
<li><strong>For i = 1:</strong>
Select the subset of indices as <code>[0, 1, 2]</code> and decrement the values at these indices by 1.
The array will become <code>[3, 1, 0, 0]</code>, which is not a Zero Array.
</pre>


<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>5</sup></code></li>
	<li><code>0 &lt;= nums[i] &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= queries.length &lt;= 10<sup>5</sup></code></li>
	<li><code>queries[i].length == 2</code></li>
	<li><code>0 &lt;= l<sub>i</sub> &lt;= r<sub>i</sub> &lt; nums.length</code></li>
</ul>

## Solution
### C++
```c++
class Solution {
public:
    bool isZeroArray(vector<int>& nums, vector<vector<int>>& queries) {
        int n = nums.size(), m = queries.size();
        vector<int> freq(n+1);

        for(int i = 0; i<m; i++) {
            int l = queries[i][0], r = queries[i][1];
            freq[l] += 1;
            freq[r+1] -= 1;
        }
        
        for(int i = 1; i<=n; i++) {
            freq[i] += freq[i-1];
        }

        for(int i = 0; i<n; i++) {
            if(freq[i] < nums[i]) return false;
        }

        return true;
    }
};
```

### Java
```java
class Solution {
    public boolean isZeroArray(int[] nums, int[][] queries) {
        int n = nums.length, m = queries.length;
        int[] freq = new int[n+1];

        for(int i = 0; i<m; i++) {
            int l = queries[i][0], r = queries[i][1];
            freq[l] += 1;
            freq[r+1] -= 1;
        }

        for(int i = 1; i<=n; i++) {
            freq[i] += freq[i-1];
        }

        for(int i = 0; i<n; i++) {
            if(freq[i] < nums[i]) return false;
        }

        return true;
    }
}
```