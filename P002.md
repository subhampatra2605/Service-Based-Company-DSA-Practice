# 🧩 Best Time to Buy & Sell Stock

## 📥 Input

* `prices = [7,1,5,3,6,4]`

---

## 📤 Output

* `5`

👉 Buy at:

```text id="v9ow4j"
1
```

👉 Sell at:

```text id="w6ydv8"
6
```

👉 Profit:

```text id="wzcx6g"
6 - 1 = 5
```

---

# 🔍 Pattern of the Problem

* **Greedy + Minimum Tracking**

👉 Core idea:

```text id="8r87p0"
Track lowest buying price seen so far
```

---

# 🐢 Brute Force Approach

### Idea:

Check every possible buy-sell pair

---

## 💻 Brute Force Code

```java id="btbss-bf-code2"
class Solution {
    public int maxProfit(int[] prices) {

        int maxProfit = 0;

        // Try every buy day
        for (int i = 0; i < prices.length; i++) {

            // Try every sell day after buy
            for (int j = i + 1; j < prices.length; j++) {

                int profit = prices[j] - prices[i];

                maxProfit = Math.max(maxProfit, profit);
            }
        }

        return maxProfit;
    }
}
```

---

## ⏱ Time Complexity

```text id="9znlg0"
O(n²)
```

---

## ❌ Shortcomings

* Checks unnecessary pairs
* Very slow for large arrays

---

# ⚡ Optimal Solution (Greedy)

---

# 💻 Java Code (Line-by-Line Explanation)

```java id="btbss-opt-code2"
class Solution {
    public int maxProfit(int[] prices) {

        // Store minimum price seen so far
        int minPrice = Integer.MAX_VALUE;

        // Store maximum profit
        int maxProfit = 0;

        // Traverse all prices
        for (int price : prices) {

            // Update minimum buying price
            if (price < minPrice) {
                minPrice = price;
            }

            // Calculate profit if sold today
            int profit = price - minPrice;

            // Update maximum profit
            if (profit > maxProfit) {
                maxProfit = profit;
            }
        }

        return maxProfit;
    }
}
```

---

# 🔄 Complete Dry Run

## Input:

```text id="hwp9u4"
[7,1,5,3,6,4]
```

---

### Step-by-step

---

### price = 7

```text id="6tlz6i"
minPrice = 7
profit = 0
maxProfit = 0
```

---

### price = 1

```text id="87kuyq"
minPrice = 1
profit = 0
maxProfit = 0
```

---

### price = 5

```text id="u9o4gj"
profit = 5 - 1 = 4
maxProfit = 4
```

---

### price = 3

```text id="5lk7jt"
profit = 3 - 1 = 2
maxProfit = 4
```

---

### price = 6

```text id="q4s5lh"
profit = 6 - 1 = 5
maxProfit = 5 ✅
```

---

### price = 4

```text id="29jlwm"
profit = 4 - 1 = 3
maxProfit = 5
```

---

# 🎯 Why This Works

👉 At every step:

```text id="ifv6xe"
Assume current day is selling day
```

👉 Best profit:

```text id="vl88n3"
current price - minimum buying price before it
```

---

# ⏱ Complexity

| Type  | Value |
| ----- | ----- |
| Time  | O(n)  |
| Space | O(1)  |

---

# ⚠️ Key Pitfalls

* ❌ Selling before buying
* ❌ Resetting maxProfit incorrectly
* ❌ Thinking multiple transactions allowed

---

# 💼 Interview Insights

👉 Whenever you see:

* “Maximum profit”
* “Buy before sell”
* “Single transaction”
* “Track best so far”

Think:

```text id="s4u1e5"
Greedy + running minimum
```

👉 Key mindset:

```text id="a01g97"
For every day,
“What if I sell today?”
```

👉 This pattern also appears in:

* Maximum Difference problems
* Kadane’s Algorithm variations
* Stock buy/sell series problems
