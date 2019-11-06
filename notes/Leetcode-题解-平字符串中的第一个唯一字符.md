## 387. [字符串中的第一个唯一字符](https://leetcode-cn.com/problems/first-unique-character-in-a-string/)

### 题目描述
给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。

**示例:**
```
案例:

s = "leetcode"
返回 0.

s = "loveleetcode",
返回 2.
```
### 代码实现
```c

int firstUniqChar(char * s){
    int freq[26]={0};
    int i,len =strlen(s);
    for (i=0;i<len;i++){
        freq[s[i]-'a']++;
    }
    for (i=0;i<len;i++){
        if ( freq[s[i]-'a'] ==1 ){
            return i;
        }
    }
    return -1;
    
}
```
