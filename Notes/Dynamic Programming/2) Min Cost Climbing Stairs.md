# 1. Min Cost Climbing Stairs

Q) You are given an integer array cost where cost[i] is the cost of ith step on a staircase. Once you pay the cost, you can either climb one or two steps. You can either start from the step with index 0, or the step with index 1. Return the minimum cost to reach the top of the floor.

## Using Recursion { T.C. - O(2<sup>n</sup>), S.C - O(N) }
```cpp
class Solution {
  public:  
    int solve(vector<int>&cost, int N){
        if(N == 0) return cost[0];
        if(N == 1) return cost[1];
        
        return min(solve(cost,N-1), solve(cost,N-2)) + cost[N];
    }
  
    int minCostClimbingStairs(vector<int>&cost ,int N) {
        //Write your code here
        return min(solve(cost,N-1), solve(cost,N-2));
    }
};
```

## Using DP Top-Down Approach { T.C. - O(2N), S.C. - O(N) }
```cpp
class Solution {
public:
    int solve(vector<int>&cost, int N, vector<int> &dp){
        if(N == 0) return cost[0];
        if(N == 1) return cost[1];
        
        if(dp[N] != -1) return dp[N];
        
        dp[N] = min(solve(cost,N-1,dp), solve(cost,N-2,dp)) + cost[N];
        
        return dp[N];
    }
    
    int minCostClimbingStairs(vector<int>& cost) {
        int N = cost.size();
        vector<int> dp(N+1,-1);
        
        return min(solve(cost,N-1,dp),solve(cost,N-2,dp)); 
    }
};
```

## Using DP Bottom-Up Approach {T.C. - O(N), S.C. - O(N) }
```cpp
class Solution {
public:    
    int minCostClimbingStairs(vector<int>& cost) {
        int n = cost.size();
        vector<int> dp(n+1);

        dp[0] = cost[0];
        dp[1] = cost[1];
        
        for(int i = 2; i < n; i++){
            dp[i] = cost[i] + min(dp[i-1],dp[i-2]);
        }

        return min(dp[n-1],dp[n-2]);
    }
};
```

## Optimizing the Space {T.C. - O(N), S.C. - O(1) }
```cpp
class Solution {
public:    
    int minCostClimbingStairs(vector<int>& cost) {
        int n = cost.size();

        int prev2 = cost[0];
        int prev1 = cost[1];
        
        for(int i = 2; i < n; i++){
            int curr = cost[i] + min(prev1,prev2);
            prev2 = prev1;
            prev1 = curr;
        }

        return min(prev1,prev2); 
    }
};
```

|S.No.|Method|TC|SC|
|-----|------|--|--|
|1.|Recursion|O(2<sup>N</sup>)|O(N)|
|2.|Top Down|O(2N)|O(N)|
|3.|Down Up|O(N)|O(N)|
|4.|Space Optimization|O(N)|O(1)|

