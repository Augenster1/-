# 本文主要记录Leetcode hot 100 刷题笔记
## 1. 两数之和
'''
python
idx = {}
for j,x in range(nums):
  if target -x in idx:
    return [idx[target-x],j]
  idx[x] = j
'''
