# 121. Best Time to Buy and Sell Stock

Given an array `prices` where `prices[i]` represents the price of a stock on the `i-th` day, your goal is to maximize profit by selecting a single day to buy one stock and a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If no profit can be achieved, return `0`.

---

## Examples

### Example 1
**Input:**  
`prices = [7,1,5,3,6,4]`  

**Output:**  
`5`  

**Explanation:**  
- Buy on day 2 (price = 1).  
- Sell on day 5 (price = 6).  
- Profit = `6 - 1 = 5`.  

Note: Buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

---

### Example 2
**Input:**  
`prices = [7,6,4,3,1]`  

**Output:**  
`0`  

**Explanation:**  
In this case, no transactions are possible, so the maximum profit is `0`.

---


## Constraints
- `1 <= prices.length <= 10^5`
- `0 <= prices[i] <= 10^4`


## Approach
Brute Force:

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int maxP = 0;
        for(int i = prices.size();i>=0;i--){
            for(int j=i;j>=0;j--)
            {
                maxP = max(maxP,prices[i]-prices[j]);
            }
        }
        return maxP;
    }
};
```
Time Complexity: O(n^2)
Space Complexity: O(1)

## Optimized Approach
```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
       
        int minSofar = INT_MAX;
        int maxP = 0;

        for(int i=0;i<prices.size();i++)
        {
            minSofar = min(minSofar,prices[i]);
            maxP = max(maxP,prices[i]-minSofar);
        }
        return maxP;
    }
};
```
Time Complexity: O(n)
Space Complexity: O(1)

```
Explanation:

You only need to keep track of:

    The minimum price so far (to buy),

    The maximum profit (current price - min price so far).

This can be solved in O(n) time and O(1) space.
```
