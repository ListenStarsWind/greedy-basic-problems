# [K 次取反后最大化的数组和](https://leetcode.cn/problems/maximize-sum-of-array-after-k-negations/)

![image-20250504140649678](https://md-wind.oss-cn-nanjing.aliyuncs.com/md/20250504140649797.png)

## 算法原理

![image-20250504141822203](https://md-wind.oss-cn-nanjing.aliyuncs.com/md/20250504141822366.png)

![image-20250504142744028](https://md-wind.oss-cn-nanjing.aliyuncs.com/md/20250504142744171.png)

## 代码编写

```cpp
class Solution {
public:
    int largestSumAfterKNegations(vector<int>& nums, int k) {
        priority_queue<int, vector<int>, greater<int>> heap(nums.begin(), nums.end());
        while(k > 0)
        {
            if(heap.top() > 0)
                k %= 2;
            if(k > 0)
            {
                int t = heap.top();
                heap.pop();
                heap.emplace(-t);
                --k;
            }
        }

        int result = 0;
        while(!heap.empty())
        {
            result += heap.top();
            heap.pop();
        }
        return result;
    }
};
```

# 完

