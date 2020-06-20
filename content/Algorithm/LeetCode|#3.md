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

### **Brute Force**

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
* **Space complexity**: One variable `max_len` is created at main function, so it is O(1) space complexity. At the helper function, we use a set `m` to store letters of a substring with at most 26 bytes of space because there are at most 26 letters in lower case. Therefore, the total space complexity is O(1).


### **How to improve the algorithm?**

Brute force works, but it's slow with O(n^3) time complexity. Now it is time to think about what the algorithm is doing. We notice that some substrings are not necessarily needed to be checked. For example, we know that string "abca" contains duplicate letter 'a', so the maximum length of substring is 3 in this case. Do we need to check subtring "bc"? Absolutely no. The substring "abc" with the maximum length already contains the substring "bc", so there is no possibility that the length of "bc" would be larger than the length of "abc". 

According to the discussion above, the brute force algorithm is slow because it wastes time in generating **useless** substrings and checking duplicate characters of them. To optimize it, I am going to introduce "sliding window" algorithm.

### **Sliding Window**

In the case that the substring `s[i:j]` contains repeating characters, the brute force algorithm `break` the for-loop of `j`, increments `i`, and again lets `j` iterate from `i` to `len(s)`. In the same case, however, the sliding window algorithm **keep**s the position of `j` and increments `i` until the substring `s[i:j]` doesn't contain duplicates. 

For example, when substrinig `s[i:j]` (i=0,j=3) is "abca", the brute force algorithm would check substring "b"(i=1,j=1) for the next iteration, but the sliding window algorithm would check substring "bca"(i=1,j=3) because `j` stays in its position. 

The pseudo-code is easy because we only need to change the main function:

```
/* helper function   **
** the same as above */

/* main function */
func longestSubstring(s string) int
{
    max_len := 0
    i := 0
    j := 0
    
    while (i < len(s) and j < len(s))
        if hasDup(s[i:j]) == False
            max_len = MAX(max_len, len(s[i:j]))
            j++
        else
            i++

    return max_len
}
```

Performance analysis:
* **Time complexity**: In the main function, we have one iteration, so time complexity is O(n). At each iteration, the helper function with time complexity of O(n) is called. Therefore, the total time complexity is O(n^2).
* **Space complexity**: It is the same as the space complexity of brute force algorithm O(1).

### **Can we optimize the sliding window algorithm?**

Yes. Why not?

The main function looks good, but how about the helper function? Is it necessary to iterate a substring in the helper function? No, because the main function has already iterated and "seen" the data. We can use a map to maintain all occurred characters of the substring `s[i:j]`. The reason why `map` is used is because `map` has O(1) time complexity in finding, adding or removing a data. 

Pseudo-code:

```
// No helper function any more

/* main function */
func longestSubstring(s string) int
{
    max_len := 0
    i := 0
    j := 0
    m := new Map[char]

    while (i < len(s) and j < len(s))
        if m.find(s[j]) == False
            max_len = MAX(max_len, len(s[i:j]))
            m.add(s[j])
            j++
        else
            m.remove(s[i])
            i++

    return max_len
}
```

Performance analysis:
* **Time complexity**: This optimized sliding window algorithm has only one iteration at the main function, so the time complexity is O(n). 
* **Space complexity**: The same, O(1).

### **Example code**
C++:
```
int lengthOfLongestSubstring(string s) {
    int max_len = 0;
    int i = 0, j = 0;
    unordered_set<char> myset;
    int len = s.length();
    
    while(i < len && j < len) {
        if (myset.find(s[j]) == myset.end()){
            max_len = max(j-i+1, max_len);
            myset.insert(s[j]);
            j++;
        } else {
            myset.erase(s[i]);
            i++;
        }
    }
    
    return max_len;
}
```

Python3:
```
def lengthOfLongestSubstring(self, s: str) -> int:
    max_len, i, j = 0,0,0
    myset = set()
    
    while(i < len(s) and j < len(s)):
        if not (s[j] in myset):
            max_len = max(max_len, len(s[i:j+1]))
            myset.add(s[j])
            j = j+1
        else:
            myset.remove(s[i])
            i = i+1
    
    return max_len
```