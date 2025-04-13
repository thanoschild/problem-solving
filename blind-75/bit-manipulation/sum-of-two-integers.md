<h2><a href="https://leetcode.com/problems/sum-of-two-integers">371. Sum of Two Integers</a></h2><h3>Medium</h3><hr><p>Given two integers <code>a</code> and <code>b</code>, return <em>the sum of the two integers without using the operators</em> <code>+</code> <em>and</em> <code>-</code>.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>
<pre><strong>Input:</strong> a = 1, b = 2
<strong>Output:</strong> 3
</pre><p><strong class="example">Example 2:</strong></p>
<pre><strong>Input:</strong> a = 2, b = 3
<strong>Output:</strong> 5
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>-1000 &lt;= a, b &lt;= 1000</code></li>
</ul>

## Solution
### C++
```c++
class Solution {
public:
    int getSum(int a, int b) {
        int carry = 0;
        while(b != 0) {
            carry = (a & b) << 1;
            a = a ^ b;
            b = carry;
        }

        return a;
    }
};
```

```c++
class Solution {
public:
    int getSum(int a, int b) {
    return log(pow(2, a) * pow(2, b))/log(2);
    }
};
```

### Java
```java
class Solution {
    public int getSum(int a, int b) {
        int carry = 0;
        while(b != 0) {
            carry = (a & b) << 1;
            a = a ^ b;
            b = carry;
        }

        return a;
    }
}
```