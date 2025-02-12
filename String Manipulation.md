## String Manipulation


## 🛠 Index
-  [💡 String Manipulation](#-Primary-queue)
-  [🃏 Leetcode](#-Leetcode)

## 💡 String Manipulation

### String Slicing in Python
- Works in _O(k)_ time complexity, where k is the slice length, without extra memory allocation
- Allows easy access to elements form the end of the string (Negative indexting)
- Enables skipping elements using s[start:end:step]
- Returns a new string without modifying the original one (Immutable and memeory efficient)


```python
s = ['h', 'e', 'l', 'l', 'o']

print(s[1:4])#ello
print(s[1:-2])#el: not include the value of -2
print(s[1:])#ello
print(s[:-3])#he
print(s[-3:])#llo
print(s[:])#hello: return a copy
print(s[::-1])#olleh: reverse
print(s[::1])#hello
print(s[::2])#hlo: move forward tow spaces 

```


## 🃏 Leetcode

- [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

- [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)
- [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
- [Valid Anagram](https://leetcode.com/problems/valid-anagram/)

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        return collections.Counter(s) == collections.Counter(t)
```

- [Group Anagrams](https://leetcode.com/problems/group-anagrams/)
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        anagrams = defaultdict(list)
        
        for s in strs:
            sorted_s = "".join(sorted(s))
            anagrams[sorted_s].append(s)

        return list(anagrams.values())
```

- [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        s_dict = {
            ')': '(', '}': '{', ']': '['
        }

        for char in s:
            if char in s_dict:
                if stack and stack[-1] == s_dict[char]:
                    stack.pop()
                else:
                    return False
            else:
                stack.append(char)

        return not stack
```

- [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = s.lower()
        s = re.sub(r'[^a-z0-9]', '', s)
        return s == s[::-1]
```

- [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)
- [Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/)





<br>   



