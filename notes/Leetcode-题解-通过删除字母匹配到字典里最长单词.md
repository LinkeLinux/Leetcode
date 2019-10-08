# 环形链表

### 题目描述
给定一个字符串和一个字符串字典，找到字典里面最长的字符串，该字符串可以通过删除给定字符串的某些字符来得到。
如果答案不止一个，返回长度最长且字典顺序最小的字符串。如果答案不存在，则返回空字符串。


**示例:**
```
示例 1:

输入:
s = "abpcplea", d = ["ale","apple","monkey","plea"]

输出: 
"apple"
示例 2:

输入:
s = "abpcplea", d = ["a","b","c"]

输出: 
"a"


```
### 代码实现
```c
char * findLongestWord(char * s, char ** d, int dSize){
    int i;
    int len;
    char *p;
    char *maxp="";
    char *src=s;
    int maxlen=0;
    if(s==NULL||d==NULL)
        return "";
    for(i=0;i<dSize;i++)
    {
        p=d[i];
        len =strlen(p);
        src=s;
        while(*p && *src ){
                if(*p==*src){
                    p++;                  
                }
                src++;   
        }
        if(*p=='\0'){
            if(len >maxlen){
                maxlen=len;
                maxp=d[i];
            }else if (len ==maxlen){
                if(strcmp(maxp,d[i])>0){
                    maxp=d[i];
                }
            }
            
        }
    }
    return maxp;
}
```