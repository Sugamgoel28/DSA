# Maximize The Cut Segments

Q) Given an integer N denoting the Length of a line segment. You need to cut the line segment in such a way that the cut length of a line segment each time is either x , y or z. Here x, y, and z are integers.After performing all the cut operations, your total number of cut segments must be maximum.

## Using Recursion { T.C. - O(2<sup>n</sup>), S.C - O(N) }
```cpp
class Solution
{    public:
    //RECURSIVE.
    int solve(int n, int x, int y, int z){
        if(n==0) return 0;
        
        if(n<0) return INT_MIN;
        
        int a = solve(n-x,x,y,z) + 1;
        int b = solve(n-y,x,y,z) + 1;
        int c = solve(n-z,x,y,z) + 1;
        
        return max(a,max(b,c));
    }
    int maximizeTheCuts(int n, int x, int y, int z)
    {
        int ans = solve(n,x,y,z);
        if(ans < 0) return 0;
        else return ans; 
    }
};
```

## Using DP Top-Down Approach { T.C. - O(2N), S.C. - O(N) }
```cpp
class Solution
{    public:
    //Top Down Approach.
    int solve(int n, int x, int y, int z,vector<int> &dp){
        if(n==0) return 0;
        if(n<0) return INT_MIN;
        
        if(dp[n] != -1) return dp[n];
        
        int a = solve(n-x,x,y,z,dp) + 1;
        int b = solve(n-y,x,y,z,dp) + 1;
        int c = solve(n-z,x,y,z,dp) + 1;
        
        dp[n] = max(a,max(b,c)); 
        return dp[n];
    }
    
    int maximizeTheCuts(int n, int x, int y, int z)
    {
        vector<int> dp(n+1,-1);
        int ans = solve(n,x,y,z,dp);
        if(ans < 0) return 0;
        else return dp[n]; 
    }
};
```

## Using DP Bottom-Up Approach {T.C. - O(N), S.C. - O(N) }
```cpp
class Solution
{    public:
    //Bottom-Up Approach
      int maximizeTheCuts(int n, int x, int y, int z)
    {
        vector<int> dp(n+1,INT_MIN);
        if(n<0) dp[n] = INT_MIN;
        dp[0] = 0;
        
        for(int i = 1; i <= n; i++){
            if(i-x >= 0)
                dp[i] = max(dp[i], dp[i-x] + 1);
            if(i-y >= 0)
                dp[i] = max(dp[i], dp[i-y] + 1);
            if(i-z >= 0)
                dp[i] = max(dp[i], dp[i-z] + 1);
        }
        if(dp[n] < 0) return 0;
        else return dp[n]; 
    }
};
```

## Optimizing the Space {T.C. - O(N), S.C. - O(1) }
- To check whether Space Optimization is possible or not, check how dp[n] varies.
- dp[n] Or do[i] depends on X, Y, and Z which are unknown.
- If we try to optimize space by replacing dp with variables, we do not know how much we have to shift in each iteration as x,y and z are unknown.
- Hence, space optimization is NOT possible.

|S.No.|Method|TC|SC|
|-----|------|--|--|
|1.|Recursion|O(2<sup>N</sup>)|O(N)|
|2.|Top Down|O(2N)|O(N)|
|3.|Down Up|O(N)|O(N)|
|4.|Space Optimization|O(N)|O(1)|
