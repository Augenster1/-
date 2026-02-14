# 本文主要记录Leetcode hot 100 刷题笔记

## 1. 两数之和

```python
def twoSum(nums, target):
    # key 存储数值，value 存储对应的索引
    idx = {}
    
    # 使用 enumerate 同时获取索引 j 和数值 x
    for j, x in enumerate(nums):
        complement = target - x
        
        # 查找差值是否在字典中
        if complement in idx:
            return [idx[complement], j]
        
        # 将当前数值和索引存入字典
        idx[x] = j
```

思路：主要是先创建一个哈希表然后能够用 if 来判断所需要的 target-x 是否在

## 2.字母异位词分组

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        d = defaultdict(list)

        for i,s in enumerate(strs):
            temp = ''.join(sorted(s)) #主要是这一步比较重要
            d[temp].append(s)
        return list(d.values())
```

思路：利用哈希表的共同key得到叠加结果的dict

## 3.最长连续序列

### 解法一：

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        nums.sort()
        ans = 0
        d = []
        for i,x in enumerate(nums):
            if i>0 and nums[i-1] == nums[i]:
                continue
            if x-nums[i-1] !=1:
                d.append(ans)
                ans = 1
            else:
                ans+=1
        d.append(ans)
        return max(d)
```

### 解法二：

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        st = set(nums)
        ans = 0
        for x in st:
            if x - 1 in st:
                continue
            y = x +1
            while y in st:
                y+=1
            ans = max(ans, y-x)
        return ans
```
思路：利用哈希表找最小的序列开始然后再依次查找更大的值
