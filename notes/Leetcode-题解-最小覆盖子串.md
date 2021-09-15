## 76. [最小覆盖子串](https://leetcode-cn.com/problems/minimum-window-substring/)

### 题目描述
给你一个字符串 s 、一个字符串 t 。返回 s 中涵盖 t 所有字符的最小子串。如果 s 中不存在涵盖 t 所有字符的子串，则返回空字符串 "" 。
注意：

对于 t 中重复字符，我们寻找的子字符串中该字符数量必须不少于 t 中该字符数量。
如果 s 中存在这样的子串，我们保证它是唯一的答案。



**示例:**
```
示例 1：

输入：s = "ADOBECODEBANC", t = "ABC"
输出："BANC"
示例 2：

输入：s = "a", t = "a"
输出："a"
示例 3:

输入: s = "a", t = "aa"
输出: ""
解释: t 中两个字符 'a' 均应包含在 s 的子串中，
因此没有符合条件的子字符串，返回空字符串。



```
### 代码实现
```go

func minWindow(s string, t string) string {
    const INT_MAX = int(^uint(0) >> 1)
    need,window := make(map[byte]int),make(map[byte]int)

    for i := 0 ;i < len(t) ;i ++{
        need[t[i]]++
    }

    start,left  := 0,0
    valid := 0
    length := INT_MAX
    for right := 0 ; right < len(s) ; right++{

        c := s[right]
        
        //if _,ok := need[c] ;ok{
            window[c] ++
            if window[c] == need[c]{
                valid++
            }
        //}
        for valid == len(need){   
            if right - left < length{
                 start = left
                length = right - left
            }

            c = s[left]
            left++
            //if _,ok := need[c] ;ok{
                if  window[c] == need[c]{
                    valid --
                }
                window[c]--
           // }
        }
    }
    if length == INT_MAX{
        return ""
    }
    return string([]byte(s)[start:start + length+1])
}
```
