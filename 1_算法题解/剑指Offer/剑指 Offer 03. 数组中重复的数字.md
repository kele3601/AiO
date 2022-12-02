---
time: 2022-11-30 10:45
tags:
	- 题解
---
## 一、题目[^1]
找出数组中重复的数字。

在一个长度为 `n` 的数组 `nums` 里的所有数字都在 `0～n-1` 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。

**示例：**
```markdown
**输入：** [2, 3, 1, 0, 2, 5, 3]
**输出：** 2 或 3
```

**限制：** `2 <= n <= 100000`
## 二、题解
### 2.1 Set 集
Set 是一个**不允许重复元素**的集合，所以可以利用唯一性来进行解题。

**示例：**
```java
public int findRepeatNumber(int[] nums) {  
    HashSet<Integer> set = new HashSet<>();  
    for (int num : nums) {  
        if (!set.add(num)){  
            return num;  
        }  
    }  
    return -1;  
}
```

### 2.2 排序
如果给出的数组是有序的，那么相同的数字都是相邻的，那么就可以减少解题难度。

**示例：**
```java
public int findRepeatNumber(int[] nums){  
    Arrays.sort(nums);  
    int temp = nums[0];  
    for (int i = 1; i < nums.length; i++) {  
        if (temp==nums[i]){  
            return temp;  
        }  
        temp = nums[i];  
    }  
    return -1;  
}
```

[^1]:[剑指 Offer 03. 数组中重复的数字 - 力扣（LeetCode）](https://leetcode.cn/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/?favorite=xb9nqhhg)