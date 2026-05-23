# 🧩 Two Sum

## 📥 Input

* `nums = [2,7,11,15]`
* `target = 9`

---

## 📤 Output

* `[0,1]`

👉 Because:

```text id="i9f3rn"
nums[0] + nums[1] = 2 + 7 = 9
```

---

# 🔍 Pattern of the Problem

* **Hashing / Complement Lookup**

👉 Core idea:

```text id="l0jlwm"
For every number,
check if target - number already exists
```

---

# 🐢 Brute Force Approach

### Idea:

Check every pair

---

## 💻 Brute Force Code

```java id="2sum-bf-code"
class Solution {
    public int[] twoSum(int[] nums, int target) {

        // Check every possible pair
        for (int i = 0; i < nums.length; i++) {

            for (int j = i + 1; j < nums.length; j++) {

                // If pair sum equals target
                if (nums[i] + nums[j] == target) {

                    // Return indices
                    return new int[]{i, j};
                }
            }
        }

        return new int[]{};
    }
}
```

---

## ⏱ Time Complexity

```text id="q9s0n6"
O(n²)
```

---

## ❌ Shortcomings

* Checks unnecessary pairs
* Very slow for large inputs

---

# ⚡ Optimal Solution (HashMap)

---

# 💻 Java Code (Line-by-Line Explanation)

```java id="2sum-opt-code"
import java.util.HashMap;

class Solution {
    public int[] twoSum(int[] nums, int target) {

        // HashMap stores:
        // number -> index
        HashMap<Integer, Integer> map = new HashMap<>();

        // Traverse array
        for (int i = 0; i < nums.length; i++) {

            // Find required complement
            int complement = target - nums[i];

            // Check if complement already exists
            if (map.containsKey(complement)) {

                // If yes, pair found
                return new int[]{map.get(complement), i};
            }

            // Store current number with index
            map.put(nums[i], i);
        }

        return new int[]{};
    }
}
```

---

# 🔄 Complete Dry Run

## Input:

```text id="49qmd2"
nums = [2,7,11,15]
target = 9
```

---

## Step-by-step

---

### i = 0

```text id="6s9kq3"
nums[i] = 2
complement = 9 - 2 = 7
```

Check:

```text id="t3c6lz"
7 in map? ❌
```

Store:

```text id="qvg0ho"
map = {2:0}
```

---

### i = 1

```text id="9j10go"
nums[i] = 7
complement = 9 - 7 = 2
```

Check:

```text id="i5f9d8"
2 in map? ✅
```

Return:

```text id="o8ps4z"
[0,1]
```

---

# 🎯 Why This Works

👉 Instead of searching entire array again:

```text id="f3b03o"
We remember previously seen numbers
```

👉 HashMap lookup:

```text id="87u7jv"
O(1)
```

---

# ⏱ Complexity

| Type  | Value |
| ----- | ----- |
| Time  | O(n)  |
| Space | O(n)  |

---

# ⚠️ Key Pitfalls

* ❌ Adding element before checking
* ❌ Returning values instead of indices
* ❌ Using same element twice

---

# 💼 Interview Insights

👉 Whenever you see:

* Pair sum
* Target sum
* Complement
* “Find two numbers”

Think:

```text id="brk4hf"
HashMap + complement lookup
```

👉 Golden pattern:

```text id="kz34aa"
target - currentElement
```

👉 This pattern is heavily used in:

* 2 Sum
* 3 Sum
* 4 Sum
* Subarray Sum Equals K
* Prefix Sum problems
