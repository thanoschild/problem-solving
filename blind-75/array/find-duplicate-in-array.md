<h2><a href="https://www.interviewbit.com/problems/find-duplicate-in-array/">Find Duplicate in Array</a></h2><h3>Easy</h3><hr>
<p>Given a read-only array of n + 1 integers between 1 and n, find one number that repeats in linear time using less than O(n) space and traversing the stream sequentially O(1) times.
If there are multiple possible answers ( like in the sample case ), output any one, if there is no duplicate, output -1</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> arr = [3, 4, 1, 4, 2]
<strong>Output:</strong> 4
<strong>Explanation:</strong> The element 4 occurs at the indices 1 and 3.
</pre>


<p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> arr = [1, 2, 3]
<strong>Output:</strong> -1
<strong>Explanation:</strong> All elements are distinct.
</pre>


<p><strong class="example">Example 3:</strong></p>
<pre><strong>Input:</strong> arr = [3, 4, 1, 4, 1]
<strong>Output:</strong> 1
<strong>Explanation:</strong> The element 1 occurs at the indices 2 and 4.
</pre>


<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= arr.length &lt;= 10<sup>5</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= arr[i] &lt;= 10<sup>9</sup></code></li>
</ul>

## Solution
### C++
```c++
int Solution::repeatedNumber(const vector<int> &arr) {
    int slow = arr[0], fast = arr[0];
    do {
        slow = arr[slow];
        fast = arr[arr[fast]];
    } while(slow != fast);
    
    slow = arr[0];
    while(slow != fast) {
        slow = arr[slow];
        fast = arr[fast];
    }
    
    return slow;
}
```

### Java
```java
public class Solution {
    public int repeatedNumber(final int[] arr) {
        int slow = arr[0], fast = arr[0];
        do {
            slow = arr[slow];
            fast = arr[arr[fast]];
        } while(slow != fast);
        
        slow = arr[0];
        while(slow != fast) {
            slow = arr[slow];
            fast = arr[fast];
        }
        
        return slow;
    }
}
```