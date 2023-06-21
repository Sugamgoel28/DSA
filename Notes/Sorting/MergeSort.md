<h1 align="center">MERGE SORT</h1>
<h4>ALGORITHM</h4>
<ul>
  <li>This is based on Divide & Conquer algorithm, We keep dividing the array to it's minimum, then we merge it again in sorted manner.</li>
  <li>Step 1: Divide array into two halves.</li>
  <li>Step 2: Sort left and right part using recursion</li>
  <li>Step 3: Merge two sorted arrays.</li><a href="https://imgbb.com/"><img src="https://i.ibb.co/NCLxcyQ/image.png" alt="image" border="0"></a><br>
<h4>MERGE SORT - CODE</h4>

```cpp

#include <bits/stdc++.h>

void mergearrays(vector<int> &arr, int mid, int s, int e){

  vector<int> temp;
  int leftIndex = s;
  int rightIndex = mid+1;

  while(leftIndex <= mid && rightIndex <= e){
   
    if(arr[leftIndex] <= arr[rightIndex])  
      temp.push_back(arr[leftIndex++]);

    else temp.push_back(arr[rightIndex++]);
  }

  while(leftIndex <= mid){
    temp.push_back(arr[leftIndex++]);
  }
  while(rightIndex <= e){
    temp.push_back(arr[rightIndex++]);
  }

  for (int i = s; i <= e; i++) {
    arr[i] = temp[i-s];
  }
}

void mergeSortfunc(vector<int> &arr, int s, int e){

  if(s>=e) return;
  int mid = s+(e-s)/2;
  
  //left part 
  mergeSortfunc(arr,s,mid);

  //right part
  mergeSortfunc(arr,mid+1,e);

  //merge2sortedarrays
  mergearrays(arr,mid,s,e);
}

void mergeSort(vector<int> &arr, int n) {
    int s = 0;
    int e = n - 1;
    mergeSortfunc(arr, s, e);
}


```

<h4>COMPLEXITIES</h4>
<ul>
  <li>Av. Time Complexity - O(N logN)</li>
  <li>Space Complexity - O(N)</li>
  <li>Best Case Time Complexity - O(N)</li>
  <li>Worst Case Time Complexity - O(N logN)</li>
</ul>
