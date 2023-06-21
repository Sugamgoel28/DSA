<h1 align="center">INSERTION SORT</h1>
<h4>ALGORITHM</h4>
<ul>
  <li>The intuition behind this algorithm is to iterate the array N-1 times, and in every iteration place the minimum element in the right place.</li>
  <li>Step 1: Consider the first element of the array as a minimum.</li>
  <li>Step 2: Iterate another loop for the rest of the elements, and figure out if any element is smaller.</li>
  <li>Step 3: Swap the elements</li>
</ul>

<img src="https://www.geeksforgeeks.org/insertion-sort/" alt="insertion-sort" border="0"></a>
<br>
&#169; codingninjas
<h4>INSERTION SORT - CODE</h4>

```cpp

#include <bits/stdc++.h> 
void insertionSort(int n, vector<int> &arr){
    // Write your code here.
    for(int i = 0; i < n; i++){
        int j = i;
        while(j>0 && arr[j-1] > arr[j]){
            swap(arr[j-1],arr[j]);
            j--;
        }
    }
}

```

<h4>COMPLEXITIES</h4>
<ul>
  <li>Av. Time Complexity - O(n<sup>2</sup>)</li>
  <li>Space Complexity - O(1)</li>
  <li>Best Case Time Complexity - O(n<sup>2</sup>)</li>
  <li>Worst Case Time Complexity - O(n<sup>2</sup>)</li>
</ul>
