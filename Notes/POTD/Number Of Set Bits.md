# NUMBER OF 1 BITS | POTD | GEEK-O-LYMPICS DAY-1

## SOLUTION:
```cpp
#include<bits/stdc++.h>
class Solution {
  public:
    int setBits(int N) {
        int count = 0;
        while(N){
            int bit = N%2;
            if(bit == 1) count++;
            N = N/2;
        }
        return count;
    }
};
```


## PROBLEM BREAKDOWN:
Let's break down the problem to find the approach:
* Input? A positive integer N.
* Output? Number of set bits ('1') in the binary equivalent of the integer.

## INTUITION:
* Convert the integer to its Binary equivalent.
* Count the number of set bits in the Binary Equivalent.

## DECIMAL to BINARY Conversion:
- **Step 1:** Divide the decimal number by 2 to get the **Result** and **Remainder**.
- **Step 2:** Repeat the division process with the **Result**, storing the **Remainder** in order.
- **Step 3:** If the Result becomes zero, the Remainder form the Binary Equivalent.
- **Step 4:** The top of the order is the Least Significant Bit (LSB), and the bottom is the Most Significant Bit (MSB).

## Example-1: Let's say N = 6 which has Binary Equivalent '110'
|S.No.| N | N/2 | N%2|
|-----|---|-----|----|
|1.|6|3|0| 
|2.|3|1|1|
|3.|1|0|1| 

### Binary = 110

## Example-2: Let's say N = 33 which has Binary Equivalent '100001'
|S.No.| N | N/2 | N%2|
|-----|---|-----|----|
|1.|33|16|1| 
|2.|16|8|0|
|3.|8|4|0|
|4.|4|2|0|
|5.|2|1|0|
|6.|1|0|1|

### Binary = 100001

## Time Complexity - O(logN) Space Complexity - O(1)

