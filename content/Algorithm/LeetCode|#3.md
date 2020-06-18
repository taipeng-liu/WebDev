## 3. Longest Substring Without Repeating Characters

The problem is available [here](https://leetcode.com/problems/longest-substring-without-repeating-characters/).

### **Description**

Given a string, find the length of the longest **substring** without repeating characters.

Example 1:

```
Input: "abcabcbb"
Output: 3
Explanation: One of the longest substrings is "abc", which has length of 3.
```

Example 2:

```
Input: "sss"
Output: 1
```

### **Solution 1 : Brute Force**

Intuitively, we can find all substrings without duplicate letters, and return the maximum length of them. This algorithm requires two core functions: (a) find all substrings; and (b) check if a given substring contains duplicate letters.

For example 1:

```
Input: "abcabcbb"
Substrings without duplicas: "abc", "bca", "cab", "bc", "cb", "a", "b", "c"
The maximum length among all the substrings is 3.
```

Pseudo-code:

```
/* helper function */
func hasDup(s string) bool
{
    //m is a set
    for i in range(0:len(s))
        if m.contains(s[i])
            return True
        else
            m.add(s[i])
    
    return False
}

/* main function */
func longestSubstring(s string) int
{
    max_len := 0

    for i in range(0:len(s))
        for j in range(i:len(s))
            if hasDup(s[i:j]) == False
                max_len = MAX(max_len, len(s[i:j]))
            else
                break

    return max_len
}
```

Let's analyse performance of the algorithm. <br>
* **Time complexity**: There are two nested iterations main function, so it's O(n^2). At each iteration, helper function `hasDup` is called, which also contains one iteration. Therefore, the total time complexity is O(n^3).
* **Space complexity**: One variable `max_len` is created at main function, so it is O(1) space complexity. At the helper function, we use a set `m` to store letters of a substring with O(n) space. Therefore, the total space complexity is O(n).


### **How to improve the algorithm?**

Brute force works, but it's slow with O(n^3) time complexity. Now it is time to think about what the algorithm is doing. We notice that some substrings are not necessarily needed to be checked. For example, we know that string "abca" contains duplicate letter 'a', so the maximum length of substring is 3 in this case. Do we need to check subtring "bc"? Absolutely no. The substring "abc" with the maximum length already contains the substring "bc", so there is no possibility that the length of "bc" would be larger than the length of "abc". 

According to the discussion above, the brute force algorithm is slow because it wastes time in generating **useless** substrings and checking duplicate characters of them. To optimize it, I am going to introduce "sliding window" algorithm.

### **Sliding Window**