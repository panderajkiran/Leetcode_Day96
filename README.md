# Leetcode_Day96
# Day 96 — Count and Say

**LeetCode 38 | Medium | Java**

## Problem

The Count and Say problem is a sequence of digit strings where each new string describes the previous string using run-length encoding.

The sequence starts with:

```text
1
11
21
1211
111221
312211
```

For a given positive integer `n`, return the nth term of this sequence.

### Example

Input:
```text
n = 4
```

Output:
```text
"1211"
```

Explanation:

- Term 1: `"1"` → One 1
- Term 2: `"11"` → Two 1s
- Term 3: `"21"` → One 2, One 1
- Term 4: `"1211"` → One 1, One 2, Two 1s

---

## Approach: Iterative Run-Length Encoding

I used an iterative approach with **StringBuilder** to generate each term.

Instead of using recursion, I started with `"1"` and generated the next string step by step.

### Steps

1. Initialize the string with `"1"`.
2. Run a loop from `2` to `n`.
3. Create a new StringBuilder for the next term.
4. Traverse the current string and compare consecutive characters.
5. If two consecutive characters are equal, increase the count.
6. If the character changes:
   - Append the count.
   - Append the previous character.
   - Reset the count to 1.
7. After the loop, append the count and the last character.
8. Update the current string with the newly generated term.
9. Return the final string.

### Java Code

```java
class Solution {
    public String countAndSay(int n) {
        String s = "1";

        for (int i = 2; i <= n; i++) {
            StringBuilder sb = new StringBuilder();
            int count = 1;

            for (int j = 1; j < s.length(); j++) {

                if (s.charAt(j) == s.charAt(j - 1)) {
                    count++;
                }
                else {
                    sb.append(count);
                    sb.append(s.charAt(j - 1));
                    count = 1;
                }
            }

            sb.append(count);
            sb.append(s.charAt(s.length() - 1));

            s = sb.toString();
        }

        return s;
    }
}
```

---

## Complexity Analysis

Let `Lᵢ` represent the length of the string generated at iteration `i`.

**Time Complexity: O(L₁ + L₂ + ... +
