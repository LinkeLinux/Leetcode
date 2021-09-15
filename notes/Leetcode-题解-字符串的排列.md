## 567. [字符串的排列](https://leetcode-cn.com/problems/permutation-in-string/)

### 题目描述
给你两个字符串 s1 和 s2 ，写一个函数来判断 s2 是否包含 s1 的排列。

换句话说，s1 的排列之一是 s2 的 子串 。



**示例:**
```
示例 1：

输入：s1 = "ab" s2 = "eidbaooo"
输出：true
解释：s2 包含 s1 的排列之一 ("ba").
示例 2：

输入：s1= "ab" s2 = "eidboaoo"
输出：false





```
### 代码实现
```go

func checkInclusion(s1 string, s2 string) bool {

    need,window := make(map[byte]int),make(map[byte]int)
    for i:= 0 ;i <len(s1) ;i++{
        need[s1[i]]++
    }

    valid := 0
    left :=0
    for right := 0 ;right < len(s2); {
        c := s2[right]
        right++
        if _,ok :=need[c];ok{
            window[c]++
        
            if window[c] == need[c]{
                valid ++
            }
        }
        for right - left >= len(s1){
            if valid == len(need){
                return true
            }
            c := s2[left]
            left++
             if _,ok :=need[c];ok{
                 if window[c] == need[c]{
                    valid--
                 }
                 window[c]--
             }
        }
    }
    return false
}
```
