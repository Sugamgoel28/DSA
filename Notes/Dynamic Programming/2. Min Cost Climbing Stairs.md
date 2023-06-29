# 1. Fibonacci Number

It is a famous sequence in which every term is the sum of the previous two terms in the sequence.
<br>
0, 1, 1, 2, 3, 5, 8, 13, 21 .... etc.

f(n) = f(n-1) + f(n-2)

Q) Given a positive integer n, find the nth fibonacci number. Since the answer can be very large, return the answer modulo 1000000007.

## Using Recursion { T.C. - O(2<sup>n</sup>), S.C - O(N) }
```cpp
 long long int nthFibonacci(long long int n){
        // code here
        if(n<=1) return n;
        return (nthFibonacci(n-1) + nthFibonacci(n-2)) % 1000000007;
}
```

## Using DP Top-Down Approach { T.C. - O(2N), S.C. - O(N) }
```cpp
class Solution {
  public:
    long long int dp[1001];
    
    long long int helper(long long int n, long long int dp[]){
        if(n<=1) return n;
        
        if(dp[n] != -1) return dp[n];
        
        dp[n] = (helper(n-1,dp) + helper(n-2,dp))%1000000007;
        return dp[n];
    }
    
    long long int nthFibonacci(long long int n){
        for(long long int i =0; i <= n; i++){
            dp[i] = -1;
        }
        
        return helper(n,dp) % 1000000007;
    }
};
```

## Using DP Bottom-Up Approach {T.C. - O(N), S.C. - O(N) }
```cpp
class Solution {
  public:
    long long int dp[1001];
    
    long long int nthFibonacci(long long int n){
        if(n<=1) return n;
        dp[0] = 0;
        dp[1] = 1;
        
        for(long long int i =2; i <= n; i++){
            dp[i] = (dp[i-1] + dp[i-2])%1000000007;
        }
        
        return dp[n];
    }
};
```

## Optimizing the Space {T.C. - O(N), S.C. - O(1) }
```cpp
class Solution {
  public:
    long long int dp[1001];
    
    long long int nthFibonacci(long long int n){
        if(n<=1) return n;
        long long int prev2 = 0;
        long long int prev1 = 1;
        
        for(long long int i =2; i <= n; i++){
            long long int curr = (prev1 + prev2)%1000000007;
            prev2 = prev1;
            prev1 = curr;
        }
        
        return prev1;
    }
};
```

|S.No.|Method|TC|SC|
|-----|------|--|--|
|1.|Recursion|O(2<sup>N</sup>)|O(N)|
|2.|Top Down|O(2N)|O(N)|
|3.|Down Up|O(N)|O(N)|
|4.|Space Optimization|O(N)|O(1)|

