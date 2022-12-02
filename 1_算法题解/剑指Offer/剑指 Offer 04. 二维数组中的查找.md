---
time: 2022-12-01 14:44
tags:
	- 题解
	- 模拟边界
---
## 一、题目[^1]
在一个 `n * m` 的二维数组中，每一行都按照从左到右 `非递减` 的顺序排序，每一列都按照从上到下 `非递减` 的顺序排序。请完成一个高效的函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

**示例：**
现有矩阵 matrix 如下：
```markdown
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
```
- 给定 target = 5，返回 true。
- 给定 target = 20，返回 false。

## 二、题解
### 2.1 暴力遍历
直接将二维数组遍历一遍，有相等就返回 `true` 。
**示例：**
```java
public boolean findNumberIn2DArray(int[][] matrix, int target) {  
    for (int i = 0; i < matrix.length; i++) {  
        for (int j = 0; j < matrix[i].length; j++) {  
            if (target == matrix[i][j]) {  
                return true;  
            }  
        }  
    }  
    return false;  
}
```

### 2.2 模拟边界
因为从左到右是**非递减**，从上到下是**非递减**的，所以可以选择右上角的数与目标值比较。如果右上角的值小于目标值，向下寻找；如果右上角的值大于，就向左寻找。

核心还是模拟二维数组的实际边界，随着寻找，将二维数组的范围逐渐缩小。

**示例：**
```java
public boolean findNumberIn2DArray(int[][] matrix, int target) {  
	// 过滤空数组
    if (matrix.length == 0 || matrix[0].length == 0) {  
        return false;  
    }  
    int x = matrix[0].length - 1, y = 0;  
    // 模拟边界
    while (x >= 0 && y <= matrix.length - 1) {  
        int temp = matrix[y][x];  
        if (target > temp) {  
            y++;  
        }  
        if (target < temp) {  
            x--;  
        }  
        if (target == temp) {  
            return true;  
        }  
    }  
    return false;  
}
```

[^1]: [剑指 Offer 04. 二维数组中的查找](https://leetcode.cn/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/)