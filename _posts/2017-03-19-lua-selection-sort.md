---
layout:     post
title:      Lua 排序算法 - 选择排序
subtitle:   Selection Sort
date:       2017-03-19
author:     ms2008
header-img: img/post-bg-miui6.jpg
catalog:    true
tags:
    - Lua
    - Algorithm
typora-root-url: ..
---

选择排序（Selection Sort）是一种简单直观的排序算法。它的工作原理如下，首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置，然后，再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。以此类推，直到所有元素均排序完毕。

选择排序的主要优点与数据移动有关。如果某个元素位于正确的最终位置上，则它不会被移动。选择排序每次交换一对元素，它们当中至少有一个将被移到其最终位置上，因此对n个元素的序列进行排序总共进行至多n-1次交换。在所有的完全依靠交换去移动元素的排序方法中，选择排序属于非常好的一种。

##### 算法步骤

1. 首先在未排序序列中找到最小元素，存放到排序序列的起始位置
2. 再从剩余未排序元素中继续寻找最小元素，然后放到已排序序列的末尾。
3. 重复第二步，直到所有元素均排序完毕。

##### 动画演示

![Alt text](/img/in-post/sort/Selection-Sort-Animation.gif)

##### Lua 实现

```lua
local function selectionSort(arr)
    for i = 1, #arr-1 do
        local idx = i
        -- 迭代剩下的元素，寻找最小的元素
        for j = i+1, #arr do
            if arr[j] < arr[idx] then
                idx = j
            end
        end
        arr[i], arr[idx] = arr[idx], arr[i]
    end
end

local list = {
    -81, -93, -36.85, -53, -31, 79, 45.94, 36, 94, -95.03, 11, 56, 23, -39,
    14, 1, -20.1, -21, 91, 31, 91, -23, 36.5, 44, 82, -30, 51, 96, 64, -41
}
selectionSort(list)
print(table.concat(list, ", "))
```
