<h1 align="center">INSERTION SORT</h1>
<h4>ALGORITHM</h4>
<ul>
  <li>The intuition behind this algorithm is to iterate the array N-1 times, and in every iteration place the minimum element in the right place.</li>
  <li>Step 1: Consider the first element of the array as a minimum.</li>
  <li>Step 2: Iterate another loop for the rest of the elements, and figure out if any element is smaller.</li>
  <li>Step 3: Swap the elements</li>
</ul>

<img src="https://i.ibb.co/j6FxCC5/selection-sort.jpg" alt="selection-sort" border="0"></a>
<br>
&#169; codingninjas
<h4>SELECTION SORT - CODE</h4>

```cpp

void selectionSort(vector<int>& arr, int n)
{   
    // Write your code here.

    for(int i = 0; i < n-1; i++){
        int minIndex = i;
        for(int j = i+1; j < n; j++){
            if(arr[j] < arr[minIndex]){
                minIndex = j;
            }
        }
        swap(arr[i],arr[minIndex]);
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
