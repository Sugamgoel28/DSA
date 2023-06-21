# BUY & SELL STOCKS


Question 1: You are given an array of prices where prices[i] is the price of a given stock on an ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day to sell that stock in the future.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.


```cpp

class Solution {
public:
    int maxProfit(vector<int>& prices) {

        int profit = 0;
        int mini = prices[0];

        for(int i = 1; i<prices.size();i++){
            int diff = prices[i] - mini;
            profit = max(diff,profit);
            mini = min(mini,prices[i]);
        }      
        return profit;
    }
};
    
```
