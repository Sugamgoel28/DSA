# Maximum sum of Non-adjacent elements

Q) Given an array Arr of size N containing positive integers. Find the maximum sum of a subsequence such that no two numbers in the sequence should be adjacent in the array.

## Using Recursion { T.C. - O(2<sup>n</sup>), S.C - O(N) }
```cpp
class Solution{
public:		
	int solve(int *arr, int n){
	    if(n == 0) return arr[0];
	    if(n<0) return 0;
	    
	    int include = solve(arr,n-2) + arr[n];
	    int exclude = solve(arr,n-1) + 0;
	    
	    return max(include,exclude);
	}
	
	int findMaxSum(int *arr, int n) {
	    // code here
	    return solve(arr,n-1);
	}
};
```

## Using DP Top-Down Approach { T.C. - O(2N), S.C. - O(N) }
```cpp
class Solution{
public:	//Top Down
	int solve(int *arr, int n, vector<int> &dp){
	    if(n == 0) return arr[0];
	    if(n<0) return 0;
	    
	    if(dp[n] != -1) return dp[n];
	    
	    int include = solve(arr,n-2,dp) + arr[n];
	    int exclude = solve(arr,n-1,dp) + 0;
	    
	    dp[n] = max(include,exclude); 
	    return dp[n];
	}	
	int findMaxSum(int *arr, int n) {
	    // code here
	    vector<int> dp(n,-1);
	    
	    return solve(arr,n-1,dp);
	}
};
```

## Using DP Bottom-Up Approach {T.C. - O(N), S.C. - O(N) }
```cpp
class Solution{
public:	//Bottom Up
	int findMaxSum(int *arr, int n) {
	    vector<int> dp(n);
	    
	    if(n<0) dp[n] = 0;
	    dp[0] = arr[0];
	    
	    for(int i = 1; i < n; i++){
	        int include = dp[i-2] + arr[i];
	        int exclude = dp[i-1] + 0;
	        dp[i] = max(include,exclude);
	    }     
	    return dp[n-1];
	}
};
```

## Optimizing the Space {T.C. - O(N), S.C. - O(1) }
```cpp
class Solution{
public:	
	//Bottom Up
	int findMaxSum(int *arr, int n) {
	    vector<int> dp(n);
	    int prev2 = 0;
	    int prev1 = arr[0];
	    
	    for(int i = 1; i < n; i++){
	        int include = prev2 + arr[i];
	        int exclude = prev1 + 0;
	        int curr = max(include,exclude);
	        
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

