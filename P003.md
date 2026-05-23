# 🧩 Running Sum of 1D Array

## 📥 Input

* `nums = [1,2,3,4]`

---

## 📤 Output

* `[1,3,6,10]`

👉 Because:

```text id="rs-ex1"
1
1+2 = 3
1+2+3 = 6
1+2+3+4 = 10
```

---

# 🔍 Pattern of the Problem

* **Prefix Sum**

👉 Core idea:

```text id="rs-core"
Current value = previous sum + current element
```

---

# 🐢 Brute Force Approach

### Idea:

For every index → calculate sum from beginning

---

## 💻 Brute Force Code

```java id="rs-bf-code"
class Solution {
    public int[] runningSum(int[] nums) {

        int[] result = new int[nums.length];

        // Calculate sum for every index
        for (int i = 0; i < nums.length; i++) {

            int sum = 0;

            // Sum from 0 to i
            for (int j = 0; j <= i; j++) {
                sum += nums[j];
            }

            result[i] = sum;
        }

        return result;
    }
}
```

---

## ⏱ Time Complexity

```text id="rs-tc1"
O(n²)
```

---

## ❌ Shortcomings

* Recalculates previous sums repeatedly
* Inefficient

---

# ⚡ Optimal Solution (Prefix Sum)

---

# 💻 Java Code (Line-by-Line Explanation)

```java id="rs-opt-code"
class Solution {
    public int[] runningSum(int[] nums) {

        // Traverse from second element
        for (int i = 1; i < nums.length; i++) {

            // Add previous running sum
            nums[i] = nums[i] + nums[i - 1];

            // Pseudocode:
            // current = current + previousSum
        }

        return nums;
    }
}
```

---

# 🔄 Complete Dry Run

## Input:

```text id="rs-dr1"
[1,2,3,4]
```

---

### i = 1

```text id="rs-dr2"
nums[1] = 2 + 1 = 3

Array:
[1,3,3,4]
```

---

### i = 2

```text id="rs-dr3"
nums[2] = 3 + 3 = 6

Array:
[1,3,6,4]
```

---

### i = 3

```text id="rs-dr4"
nums[3] = 4 + 6 = 10

Array:
[1,3,6,10]
```

---

# 🎯 Why This Works

👉 Every element stores:

```text id="rs-why"
sum till previous index
```

So:

```text id="rs-why2"
current running sum
= current number + previous running sum
```

---

# ⏱ Complexity

| Type  | Value |
| ----- | ----- |
| Time  | O(n)  |
| Space | O(1)  |

---

# ⚠️ Key Pitfalls

* ❌ Starting loop from 0
* ❌ Using extra array unnecessarily
* ❌ Forgetting previous accumulated sum

---

# 💼 Interview Insights

👉 Whenever you see:

* Cumulative sum
* Range sum
* Continuous sum
* Sum till index

Think:

```text id="rs-insight"
Prefix Sum
```

👉 Golden relationship:

```text id="rs-formula"
prefix[i] = prefix[i-1] + nums[i]
```

👉 This pattern is heavily used in:

* Subarray Sum problems
* Range Query problems
* Running Sum
* Prefix/Suffix problems
