<h1 align="center">BUBBLE SORT</h1>
<h4>ALGORITHM</h4>
<ul>
  <li>The intuition behind this algorithm is to iterate the array N-1 times, and in every iteration place the i<sup>th</sup> Largest element gets placed in the right place.</li>
  <li>Step 1: Compare first two elements</li>
  <li>Step 2: If the former is greater than the Latter then swap, else move ahead.</li>
  <li>Step 3: Keep comparing in a similar fashion for further iterations.</li>
</ul>

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



