# [买卖股票的最佳时机 II](https://leetcode.cn/problems/best-time-to-buy-and-sell-stock-ii/)

![image-20250503133838842](https://md-wind.oss-cn-nanjing.aliyuncs.com/md/20250503133838912.png)

## 算法原理

![image-20250503135803930](https://md-wind.oss-cn-nanjing.aliyuncs.com/md/20250503135804111.png)

## 代码编写

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int result = 0;
        int size = prices.size();
        prices.emplace_back(0);
        for(int i = 0, j = 0; j < size; )
        {
            if(prices[j+1] > prices[j]) ++j;
            else
            {
                result += prices[j] - prices[i];
                i = ++j;
            }
        }
        return result;
    }
};

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int result = 0;
        int size = prices.size();
        prices.emplace_back(0);
        for(int i = 0, j = 0; j < size; ++j)
        {
            if(prices[j+1] <= prices[j])
            {
                result += prices[j] - prices[i];
                i = j + 1;
            }
        }
        return result;
    }
};

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int result = 0;
        int size = prices.size();
        for(int i = 0, j = 1; j < size; ++i, ++j)
        {
            if(prices[j] > prices[i])
                result += prices[j] - prices[i];
        }
        return result;
    }
};
```

## 完