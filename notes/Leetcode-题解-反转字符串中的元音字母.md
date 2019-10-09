## 345. [反转字符串中的元音字母](https://leetcode-cn.com/problems/reverse-vowels-of-a-string/submissions/)

### 题目描述
编写一个函数，以字符串作为输入，反转该字符串中的元音字母。

**示例:**
```
示例 1:

输入: "hello"
输出: "holle"
示例 2:

输入: "leetcode"
输出: "leotcede"
```
### 代码实现
```c

char * reverseVowels(char * s){
    char *start =s;
    char tmp;
    char *end =s+strlen(s)-1;
    while(start <end)
    {
        if (*start =='a'||*start =='A'||*start =='e'||*start =='E'||*start =='i'||*start =='I'||*start =='o'||*start =='O'||*start =='u'||*start =='U'){
            if ((*end !='a')&&(*end !='A') &&(*end !='e') &&(*end !='E')&&(*end !='i')&&(*end !='I') &&(*end !='o')&&(*end !='O') &&(*end !='u')&&(*end !='U'))
                end --;
            else {
                //swap(*start,*end)
                tmp =*start;
                *start =*end;
                *end =tmp;
                end --;
                start ++;
            }    
        }
        else{
            start ++;
        }
    }
    return s;
}
```
