<h1 align="center">MERGE SORT</h1>
<h4>ALGORITHM</h4>
<ul>
  <li>This is based on Divide & Conquer algorithm, We keep dividing the array to it's minimum, then we merge it again in sorted manner.</li>
  <li>Step 1: Divide array into two halves.</li>
  <li>Step 2: Sort left and right part using recursion</li>
  <li>Step 3: Merge two sorted arrays.</li>
<img src="https://i.ibb.co/X3Jz7Cn/image.png" alt="image" border="0">
<br>
<h4>MERGE SORT - CODE</h4>

```cpp

#include <bits/stdc++.h>

vector<int> mergearrays(int n, vector<int> arr, int mid, int s, int e){

  vector<int> temp;
  int leftIndex = s;
  int rightIndex = e;

  while(leftIndex <= mid && rightIndex <= e){
    
  }
  
}

void mergeSortfunc(int n, vector<int> &arr, int s, int e){

  if(s>=e) return;
  int mid = e+(s-e)/2;
  
  //left part 
  mergeSortfunc(n,arr,s,mid);

  //right part
  mergeSortfunc(n,arr,mid+1,e);

  //merge2sortedarrays
  mergearrays(n,arr,mid,s,e);
}
void mergeSort(int n, vector<int> &arr){
    // Write your code here.
    int s = 0;
    int e = n-1;
    mergeSortfunc(n,arr,s,e)
}

```

<h4>COMPLEXITIES</h4>
<ul>
  <li>Av. Time Complexity - O(n<sup>2</sup>)</li>
  <li>Space Complexity - O(1)</li>
  <li>Best Case Time Complexity - O(n<sup>2</sup>)</li>
  <li>Worst Case Time Complexity - O(n<sup>2</sup>)</li>
</ul>
