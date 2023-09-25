Tag: `Bit Manipulation` 
## Note
1. 今天的題目有很多花樣可以變
2. 第一種是用`python`的`counter`, 把字串建立成`dict`, 然後比對
3. 第二種是用`sorted`排序之後比對
4. 前兩種感覺不夠厲害, 都是用別人的工具, 第三種是把兩個字串中的字元的ASCII互相抵消, 剩下的數字就是多出來的字元的ASCII
5. 其實可以用+-下去算, 但有個解答是用異或`^`下去算, 看起來十分厲害

## Code
### Ans 1:
    class Solution:
        def findTheDifference(self, s: str, t: str) -> str:
            
            dict = Counter(s)
            for i in t:
                dict[i] -= 1
            for key, value in dict.items():
                if value == -1:
                    return key
### Ans 2:
    class Solution:
        def findTheDifference(self, s: str, t: str) -> str:
            
            s = sorted(s)
            t = sorted(t)
            
            for i in range(len(s)):
                if s[i] != t[i]:
                    return t[i]
            
            return t[-1]
### Ans 3:
    class Solution:
        def findTheDifference(self, s: str, t: str) -> str:
            res = 0
            for c in s:
                res ^= ord(c)
            for c in t:
                res ^= ord(c)
            return chr(res)

## Complexity analysis
### Time complexity: O(n)

### Space complexity: O(1)
