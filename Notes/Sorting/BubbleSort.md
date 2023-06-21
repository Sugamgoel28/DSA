<h1 align="center">BUBBLE SORT</h1>
<h4>ALGORITHM</h4>
<ul>
  <li>The intuition behind this algorithm is to iterate the array N-1 times, and in every iteration place the i<sup>th</sup> Largest element gets placed in the right place.</li>
  <li>Step 1: Compare first two elements</li>
  <li>Step 2: If the former is greater than the Latter then swap, else move ahead.</li>
  <li>Step 3: Keep comparing in a similar fashion for further iterations.</li>
</ul>

<img align="center" src="https://i.ibb.co/bRdwskL/bubble-short.png" alt="Bubble Sort Visualize">

<h4>BUBBLE SORT - CODE</h4>

```cpp

void bubbleSort(vector<int>& arr, int n)
{   
    // Write your code here.
    for(int i = 0; i < n-1; i++){ //Else for(i=1; i<n;i++) 
      // Total N-1 Rounds
        for(int j = 0; j < n-(i+1); j++){ //Else for (j=0;j<n-i;j++)
            if(arr[j] > arr[j+1])
                swap(arr[j],arr[j+1]);
        }
    }
}

```

<h4>OPTIMISATION</h4>
<ul>
  <li>The best case would be if the array is already sorted. However, as per the current code, there would be N-1 rounds and N-1 comparisons for each round, even in best case.</li>
  <li>This suggests that the code can be further optimized. If we have not swapped a single element in the first round, we do not need to go for the next rounds.</li>
  <li>This can be achieved by initializing a bool variable, that will check if any swapping was done in the first round. If no swapping is done then it will break the loop.</li>
  <li>In this manner, the time complexity in the best case will be O(n) instead of O(n<sup>2</sup>)/./li>
</ul>


<h4>BUBBLE SORT - OPTIMIZED CODE</h4>

```cpp
#include <bits/stdc++.h> 
void bubbleSort(vector<int> &arr, int n){
  for(int i = 0; i <n-1; i++){
    bool Isswap = false;
    for(int j = 0; j < n-i-1;j++){
          if(arr[j] > arr[j+1]){
              Isswap = true;
              swap(arr[j],arr[j+1]);
              }
          }
      if(Isswap == false){
      break;
    }
  }
}
```

<h4>COMPLEXITIES</h4>
<ul>
  <li>Av. Time Complexity - O(n<sup>2</sup>)</li>
  <li>Space Complexity - O(1)</li>
  <li>Best Case Time Complexity - O(n)</li>
  <li>Worst Case Time Complexity - O(n<sup>2</sup>)</li>
</ul>



