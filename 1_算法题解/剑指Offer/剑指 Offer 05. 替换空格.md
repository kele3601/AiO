---
time: 2022-12-01 16:48
tags:
	- 题解
---
## 一、题目[^1]
请实现一个函数，把字符串 `s` 中的每个空格替换成"%20"。

**示例：**
```markdown
**输入：**s = "We are happy."
**输出：**"We%20are%20happy."
```
## 二、题解
### 2.1 遍历替换
遍历一次字符串，然后将 `=` 替换成 `%20` 即可。

**示例：**
```java
public String replaceSpace(String s) {  
    String str = "";  
    for (int i = 0; i < s.toCharArray().length; i++) {  
        if (' ' == s.charAt(i)) {  
            str += "%20";  
        } else {  
            str += s.charAt(i);  
        }  
    }  
    return str;  
}
```

**时间复杂度：** O（N）
**空间复杂度：** O（N），字符串不可变，所以每一次都会新增一个String对象。

[^1]:[剑指 Offer 05. 替换空格 - 力扣（LeetCode）](https://leetcode.cn/problems/ti-huan-kong-ge-lcof/?favorite=xb9nqhhg)