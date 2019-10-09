## 680. [验证回文字符串II](https://leetcode-cn.com/problems/valid-palindrome-ii/)

### 题目描述
给定一个非空字符串 s，最多删除一个字符。判断是否能成为回文字符串。

**示例:**
```
示例 1:

输入: "aba"
输出: True
示例 2:

输入: "abca"
输出: True
解释: 你可以删除c字符。
```
### 代码实现
```c
bool judge(char *s,int i,int j)
{
    while(i<j){
         if (s[i]==s[j]){
            j--;
            i++;
         }else{
             return false;
         }
    }
    return true;
}
bool validPalindrome(char * s){
    int i=0;
    int end =strlen(s)-1;
    while(i<end){
        if (s[i]==s[end]){
            end--;
            i++;
        }
        else{
             return (judge(s,i+1,end)||judge(s,i,end-1));
        }
    }
    return true;
}
```
