## 438. [找到字符串中所有字母异位词](https://leetcode-cn.com/problems/find-all-anagrams-in-a-string/)

### 题目描述
给定两个字符串 s 和 p，找到 s 中所有 p 的 异位词 的子串，返回这些子串的起始索引。不考虑答案输出的顺序。

异位词 指字母相同，但排列不同的字符串。





**示例:**
```
示例 1:

输入: s = "cbaebabacd", p = "abc"
输出: [0,6]
解释:
起始索引等于 0 的子串是 "cba", 它是 "abc" 的异位词。
起始索引等于 6 的子串是 "bac", 它是 "abc" 的异位词。
 示例 2:

输入: s = "abab", p = "ab"
输出: [0,1,2]
解释:
起始索引等于 0 的子串是 "ab", 它是 "ab" 的异位词。
起始索引等于 1 的子串是 "ba", 它是 "ab" 的异位词。
起始索引等于 2 的子串是 "ab", 它是 "ab" 的异位词。




```
### 代码实现
```go

func findAnagrams(s string, p string) []int {

    need, window := make(map[byte]int), make(map[byte]int)
	for i := 0; i < len(p); i++ {
		need[p[i]]++
	}
    var res = []int{}
	valid := 0
	left := 0
	for right := 0; right < len(s); {
        c := s[right]
        
        right++
		if _, ok := need[c]; ok {
			window[c]++

			if window[c] == need[c] {
				valid++
			}
		}
        for right - left >= len(p){
            if valid == len(need){
                res = append(res,[]int{left}...)
            }
            c := s[left]
            left++
            if _, ok := need[c]; ok {
                if window[c] == need[c]{
                    valid --
                    
                }
                window[c]--
            }
            
        }
    }
    return res
}
```
