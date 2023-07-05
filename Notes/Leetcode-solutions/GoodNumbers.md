
# COUNT GOOD NUMBERS
- Good numbers -> A number with even digits at even indices and prime numbers at odd indices.
- Total Even digits -> five { 0, 2, 4, 6, 8 }, Total Prime Numbers -> Four {2,3,5,7} 

# Problem Breakdown
- Input -> 'N' a positive integer denoting the length number of digits in number.
- Output -> Total possible good numbers.
> *Things to Remember: 0-based indexing & Leading zeroes allowed.*  
## INTUITION:
- At even indices, the possible ways to fill it will be 5.
- At odd indices, the possible ways to fill it will be 4.
- We need to count total even and odd indices.

### Example 1: Let's say N = 5, Total Ways - 5 X 4 X 5 X 4 X 5 = 2000

|Index Number->|4|3|2|1|0|
|-|-|-|-|-|-|
|Is the index <br>Even or Odd? |E|O|E|O|E|
|Total Possible ways<br> to fill this index|5|4|5|4|5| 
|What are the Possible <br>values at this index?|0<br> 2<br> 4<br> 6<br> 8|2<br> 3<br> 5<br>7|0 <br>2<br> 4<br> 6<br> 8|2<br> 3<br> 5<br>7|0 <br>2<br> 4<br> 6<br> 8|


### Example 2: Let's say N = 3, Total Ways - 5 X 4 X 5 = 100

|Index Number->|2|1|0|
|-|-|-|-|
|Is the index <br>Even or Odd? |E|O|E|
|Total Possible ways<br> to fill this index|5|4|5| 
|What are the Possible <br>values at this index?|0 <br>2<br> 4<br> 6<br> 8|2<br> 3<br> 5<br>7|0 <br> 2<br> 4<br> 6<br> 8|

## BRUTE FORCE APPROACH - Using loop 
### T.C. - O(N), S.C. - O(1)

```cpp
#define MOD 1000000007 
class Solution {
public:
  //Using Loop -> TLE;
    int countGoodNumbers(long long n) {
      long long ans = 1;
      while(n > 0){
        n--;
        if(n%2 == 0){
          ans = (ans * 5) % MOD;
        }
        else ans = (ans * 4) % MOD;
      }
        return ans;  
    }
};
```
## Using Recursion { T.C. - O(2<sup>n</sup>), S.C - O(N) }
```cpp
class Solution {
public:
  //Using
   long long power(long long x, long long n) {

    if (n == 0) return 1;

    if (n % 2 == 0) {
        long long temp = power((x * x) % MOD, n / 2);
        return temp % MOD;
    } else {
        long long temp = power((x * x) % MOD, (n - 1) / 2);
        return (x * temp) % MOD;
    }
}

    int countGoodNumbers(long long n) {
        long long odd = power(4,n/2) % MOD; 
        long long even = power(5,n-n/2)%MOD;
        
        return (odd*even)%MOD;
    }
};
```


> *NOTE: If I have overlooked any information or if you have any questions, please leave a comment. Please select the Upvote button if you find this useful.🙏✨*

![Please Upvote.png](https://assets.leetcode.com/users/images/d2694b8b-cafd-4253-b40a-6ad4485dda7b_1687511263.672226.png)
