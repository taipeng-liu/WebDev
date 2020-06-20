## 5. Longest Palindromic Substring

The problem is available [here](https://leetcode.com/problems/longest-palindromic-substring/).

## **Description**

Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

Example 1:
```
Input: "babad"
Output: "bab"
Note: "aba" is also valid.
```

Example 2:
```
Input: "tppl"
Output: "pp"
```

## **Brute Force**

According to description of the problem, we can seperate the algorithm into two main parts/functions: (a) find out all substrings; and (b) if a substring is a palindromic substring and is longer than other palindromic substrings, return it.

Pseudo-code:
```
/* helper function */
func isPalindrome(s string) bool {
    for i in range(0:len(s)/2)
        if s[i] != s[len(s)-i-1]
            return False

    return True
}

/* main function */
func longestPalindrome(s string) string {
    max_len := 0
    start := 0

    for i in range(0:len(s))
        for j in range(i:len(s))
            if isPalindrome(s[i:j]) and len(s[i:j]) > max_len
                max_len = len(s[i:j])
                start = i

    return s[start:start+max_len]
}
```

This is a very straightforward algorithm, but the performance is bad:
* **Time complexity**: The main function has two iterations over the string `s`. Suppose the total length of `s` is n, then the time complexity is O(n^2). At each iteration, helper function `isPalindrome()` is called to traverse the substring checking if it is palindromic. The time complexity of helper function is O(n), and therefore, the total time complexity is O(n^3).

* **Space complexity**: We keep track of the longest palindromic substring by storing its length and start index. Only 2 bytes of memory is needed to store those variables, so the space complexity is O(1).

## **How can we improve brute force algorithm?**

Let's try to manually run the program with an example of string `abcba`. The brute force algorithm is traversing all substrings in this order:

```
 a, ab, abc, abcb, abcba
 b, bc, bcb, bcba
 c, cb, cba
 b, ba
 a
 ```

 At the first row, only the last substring is a valid palindrome, but before it the program is checking 4 non-palindrome. Obviously, the algorithm doesn't consider the symmetricity of palindrome, so the efficiency is low. If we take the special structure of palindrome into consideration, the algorithm should traverse the substrings like this:
 ```
 a, ab
 b, abc, bc
 c, bcb, abcba, cb
 b, cba, ba
 a
 ```

## **O(n^2) Solution**

You may find the difference between two examples above. The original solution fixes the left pointer `i` and moves the right pointer `j` to extract substrings. The new algorithm, however, is taking advantages of symmetricity by fixing a middle pointer and expanding the edge pointer. The new one is more efficient in finding a palindrome because if a substring "aXa" is a palindrome, then the shorter substring "X" must also be a palindrome, and vise versa. 

There are two patterns of symmetricity: (a) a palindrome with odd number of characters, such as "abcba"; and (b) a palindrome with even number of characters, such as "abba". Therefore, we need to set two middle pointers. For the pattern (a), the middle pointers are both 'c', and for (b), the middle pointers are 'b's at left side and right side.

Pseudo-code:
```
/* helper function */
// This function returns length of longest 
// palindrome for given middle pointers.
func sizeofLongestPalindrome(s string, middle_l int, middle_r int) int {
    if (middle_l < 0 or middle_r > len(s)-1 or s == "")
        return 0

    while (middle_l >= 0 and middle_r <= len(s)-1)
        if (s[middle_l] != s[middle_r])
            break
        middle_l--
        middle_r++

    return middle_r - middle_l - 1
}

/* main function */
func longestPalindrome(s string) string {
    max_len := 0 // maximum length of longest palindrome
    start   := 0 // starting position of longest palindrome
    end     := 0 // ending position of longest palindrome

    for i in range(0:len(s))
        //Check pattern (a)
        length_a := sizeofLongestPalindrome(s, i, i)
        //Check pattern (b)
        length_b := sizeofLongestPalindrome(s, i, i+1)

        temp_max_len := MAX(length_a, length_b)

        if (temp_max_len > max_len)
            max_len = temp_max_len
            start   = i - (temp_max_len-1)/2
            end     = i + temp_max_len/2

    return s[start:end+1] // exclude s[end+1]
}
```

Performance analysis:
* **Time complexity**: O(n) for one iteration at main function, and O(n) for the helper function. Therefore, the total time complexity is O(n^2).
* **Space complexity**: O(1).

## **Example Code**

C++:
```
short sizeofLongestPalindrome(string s, short middle_l, short middle_r) {
    short len = s.length();
    
    if (len == 0 || middle_l < 0 || middle_r > len-1)
        return 0;
    while (middle_l >= 0 && middle_r <= len-1) {
        if (s[middle_l] != s[middle_r])
            break;
        middle_l--;
        middle_r++;
    }
    return middle_r - middle_l - 1;
}

string longestPalindrome(string s) {
    short max_len = 0;
    short start = 0;
    short length_a, length_b, temp_max_len;
    
    for (short i = 0; i < s.length(); i++){
        length_a = sizeofLongestPalindrome(s, i, i);
        length_b = sizeofLongestPalindrome(s, i, i+1);
        temp_max_len = max(length_a, length_b);
        
        if (temp_max_len > max_len) {
            max_len = temp_max_len;
            start = i - (max_len-1)/2;
        }
    }
    
    return s.substr(start, max_len);
}
```

*Note*: I am using `short` because the maximum size of s is 1000;

Python3:
```
def sizeofLongestPalindrome(self, s: str, middle_l: int, middle_r: int) -> int:
    if len(s) == 0 or middle_l < 0 or middle_r > len(s)-1:
        return 0
    while(middle_l >=0 and middle_r <= len(s)-1):
        if (s[middle_l] != s[middle_r]):
            break
        middle_l -= 1
        middle_r += 1
        
    return middle_r - middle_l - 1

def longestPalindrome(self, s: str) -> str:
    max_len = 0
    start = 0
    end = 0
    
    for i in range(len(s)):
        length_a = self.sizeofLongestPalindrome(s, i, i)
        length_b = self.sizeofLongestPalindrome(s, i, i+1)
        
        temp_max_len = max(length_a, length_b)
        
        if (temp_max_len > max_len):
            max_len = temp_max_len
            start = i - (max_len-1)//2
            end = i + max_len//2
            
    return s[start:end+1]
```