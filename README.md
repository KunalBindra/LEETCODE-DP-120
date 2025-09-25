# LEETCODE-DP-120
This is a **Dynamic Programming (bottom-up)** solution to the **Triangle Minimum Path Sum** problem.

Let’s dry run step by step with an example triangle:

```
triangle = [
     [2],
    [3,4],
   [6,5,7],
  [4,1,8,3]
]
```

---

### Step 1: Setup

* `height = triangle.size() = 4`
* `dp = new int[5][5]` → A 2D array initialized with zeros.

---

### Step 2: Iteration

We iterate from **bottom row (level = 3) to top row (level = 0)**.

#### Level = 3 (last row: \[4,1,8,3])

```
dp[3][0] = 4 + min(dp[4][0], dp[4][1]) = 4 + 0 = 4
dp[3][1] = 1 + min(dp[4][1], dp[4][2]) = 1 + 0 = 1
dp[3][2] = 8 + min(dp[4][2], dp[4][3]) = 8 + 0 = 8
dp[3][3] = 3 + min(dp[4][3], dp[4][4]) = 3 + 0 = 3
```

Now:

```
dp[3] = [4, 1, 8, 3]
```

---

#### Level = 2 (row: \[6,5,7])

```
dp[2][0] = 6 + min(dp[3][0], dp[3][1]) = 6 + min(4,1) = 7
dp[2][1] = 5 + min(dp[3][1], dp[3][2]) = 5 + min(1,8) = 6
dp[2][2] = 7 + min(dp[3][2], dp[3][3]) = 7 + min(8,3) = 10
```

Now:

```
dp[2] = [7, 6, 10]
```

---

#### Level = 1 (row: \[3,4])

```
dp[1][0] = 3 + min(dp[2][0], dp[2][1]) = 3 + min(7,6) = 9
dp[1][1] = 4 + min(dp[2][1], dp[2][2]) = 4 + min(6,10) = 10
```

Now:

```
dp[1] = [9, 10]
```

---

#### Level = 0 (row: \[2])

```
dp[0][0] = 2 + min(dp[1][0], dp[1][1]) = 2 + min(9,10) = 11
```

---

### Step 3: Final Answer

```
return dp[0][0] = 11
```

✅ Minimum path sum = **11**
(Path is 2 → 3 → 5 → 1)

---
