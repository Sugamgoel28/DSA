
# 3. Climbing Stairs

Q) You are climbing a staircase. It takes n steps to reach the top. Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

## Using Recursion { T.C. - O(2<sup>n</sup>), S.C - O(N) }
```cpp
class Solution {
public:
    int solve(int n){
        if(n==0) return 1;
        if(n<0) return 0;

        return solve(n-1) + solve(n-2);
    }
    
    int climbStairs(int n) {
        //Recursion
        int ways = solve(n-1) + solve(n-2);
        return ways;
    }
};
```

## Using DP Top-Down Approach { T.C. - O(2N), S.C. - O(N) }
```cpp
class Solution {
public:
    int solve(int n,vector<int> &dp){
        if(n==0) return 1;
        if(n<0) return 0;

        if(dp[n] != -1) return dp[n];

        dp[n] = solve(n-1,dp) + solve(n-2,dp); 
        return dp[n];
    }

    int climbStairs(int n) {
        //Top-Up Approach
        vector<int> dp(n+1,-1);
        int ways = solve(n-1,dp) + solve(n-2,dp);
        return ways;
    }
};
```

## Using DP Bottom-Up Approach {T.C. - O(N), S.C. - O(N) }
```cpp
class Solution {
public:
    int climbStairs(int n) {
        //Bottom-Up Approach
        vector<int> dp(n+1,-1);
        if(n==0 || n == 1) return 1;
        if(n<0) return 0;

        dp[0] = 1;
        dp[1] = 1;

        for(int i = 2; i<n;i++){
            dp[i] = dp[i-1] + dp[i-2];
        }

        return dp[n-1] + dp[n-2];
    }
};
```

## Optimizing the Space {T.C. - O(N), S.C. - O(1) }
```cpp
class Solution {
public:
    int climbStairs(int n) {
        //Space Optimization

        if(n==0 || n == 1) return 1;
        if(n<0) return 0;

        int prev2 = 1;
        int prev1 = 1;

        for(int i = 2; i<n;i++){
            int curr = prev1 + prev2;
            prev2 = prev1;
            prev1 = curr;
        }

        return prev1 + prev2;
    }
};
```

|S.No.|Method|TC|SC|
|-----|------|--|--|
|1.|Recursion|O(2<sup>N</sup>)|O(N)|
|2.|Top Down|O(2N)|O(N)|
|3.|Down Up|O(N)|O(N)|
|4.|Space Optimization|O(N)|O(1)|

