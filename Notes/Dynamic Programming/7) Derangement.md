# Disarrangement of balls

Q) You are given N balls numbered from 1 to N and there are N baskets numbered from 1 to N in front of you, the ith basket is meant for the ith ball. Calculate the number of ways in which no ball goes into its respective basket.

## Using Recursion { T.C. - O(2<sup>n</sup>), S.C - O(N) }
```cpp
class Solution{
public:
    
    #define Mod 1000000007;
   //Using Recursion
    long int disarrange(int N){
        if(N <= 1) return 0;
        if(N == 2) return 1;
        
        return (N-1)*(disarrange(N-1) + disarrange(N-2))%Mod;
    }
};
```

## Using DP Top-Down Approach { T.C. - O(2N), S.C. - O(N) }
```cpp
class Solution{
public:
    #define Mod 1000000007;
   //Using Recursion
   
   long int solve(int N, vector<int> &dp){
        if(N <= 1) return 0;
        if(N == 2) return 1;
        
        if(dp[N] != -1) return dp[N];
        
        dp[N] = (N-1)*(solve(N-1,dp) + solve(N-2,dp))%Mod;
        return dp[N]; 
   }
   
    long int disarrange(int N){
        vector<int> dp(N+1,-1);
        return solve(N, dp);
    }
};
```

## Using DP Bottom-Up Approach {T.C. - O(N), S.C. - O(N) }
```cpp
class Solution{
public:
    #define Mod 1000000007;
   //Using Bottom Up
     long int disarrange(int N){
        vector<long int> dp(N+1,0);
        dp[1]=0;
        dp[2]=1;
        
        for(int i = 3; i<=N; i++){
            long int first = dp[i-1] % Mod;
            long int second = dp[i-2] % Mod;
            
            long int sum = (first + second)%Mod;
            long int ans = ((i-1)*sum)%Mod;
            
            dp[i] = ans;
        }
        return dp[N];
    }
};
```

## Optimizing the Space {T.C. - O(N), S.C. - O(1) }
```cpp
class Solution{
public:
    #define Mod 1000000007;
   //Using Bottom Up
     long int disarrange(int N){
        vector<long int> dp(N+1,0);
        int prev2 = 0;
        int prev1 = 1;    
        for(int i = 3; i<=N; i++){
            long int first = prev1 % Mod;
            long int second = prev2 % Mod;
            
            long int sum = (first + second)%Mod;
            long int ans = ((i-1)*sum)%Mod;
            
            dp[i] = ans;
            prev2 = prev1;
            prev1 = ans;
        }
        return prev1;
    }
};
```

## Using Formula of Derangement -> TLE
```cpp
class Solution{
public:
    #define Mod 1000000007;
    long int fact(int N){
        long int ans = 1;
        while(N >= 1){
            ans = ans * N;
            N--;
        }
        return ans%Mod;
    }
    double Sum(int N){
        double ans = 0;
        for(int i = 0; i <= N;i++){
            ans += pow(-1,i)/fact(i);
        }
        return ans;
    }
    long int disarrange(int N){
        long int ans = fact(N)*Sum(N);
        return ans%Mod;
    }
};
```

|S.No.|Method|TC|SC|
|-----|------|--|--|
|1.|Recursion|O(2<sup>N</sup>)|O(N)|
|2.|Top Down|O(2N)|O(N)|
|3.|Down Up|O(N)|O(N)|
|4.|Space Optimization|O(N)|O(1)|
