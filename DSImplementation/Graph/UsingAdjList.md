<h1>Implementation of Graphs using Adjacency List</h1>

<h5>Graph Components</h5>
<ul>
<li>Nodes/Vertices --> Have some data</li>
<li>Edges --> Link between two nodes</li>
</ul>
<h5>Graph Types</h5>
<ul>
  <li>Directed Graph (Having direction)</li>
  <li>Undirected Graph (Not having direction)</li>
</ul>

<h5>Adjacency List:</h5>
<ul>
  <li>Meaning: An array of Linked Lists -> Adjacency List</li>
  <li>Size of array = Number of vertices</li>
</ul> <hr>
<h3>Implementation using Adj List & Unordered Map:</h3>
<ol>
  <li>Graph is represented by showing each node and all links of that node.<br>
<i>(Har node par jao, or btao ki kis kis node se connected hai, ye puri mapping ek graph ko represent kregi)</i></li>
  <li>unordered_map&lt;int, list&lt;int&gt;&gt; <br>
    first (int) -> Value of node, <br>
    second (list) -> list of all the node with which first node is linked</li>
</ol>

```cpp
#include<iostream>
#include<bits/stdc++.h>
using namespace std;

class Graph{
    public:
    unordered_map<int,list<int>> adjList;
    void addEdge(int u, int v, bool dir);
    void printGraph();
    // u ---> Pehle node ka data
    // v ---> Dusre node ka data
    // dir ---> U node se V node ki direction.
    // Directed Graph -> bool dir = 1;
    // Undirected Graph -> bool dir = 0;

};

void Graph:: addEdge(int u, int v, bool dir){
    adjList[u].push_back(v);
    if(dir == 0){
        adjList[v].push_back(u);
    }
}

void Graph:: printGraph(){
    for(auto i: adjList){
        cout<< i.first <<"->";
        for(auto j: i.second){
            cout<< j <<",";
        }
        cout<<endl;
    }
}

int main(){

    int edgesNum;
    cout<<"Enter the number of edges"<<endl;
    cin>>edgesNum;

    Graph g;

    for(int i = 0; i < edgesNum; i++){
        int u, v;
        cout<<"Enter the edges"<<endl;
        cin >> u >> v;
        g.addEdge(u,v,0);
    }

    //printing the graph
    g.printGraph();

    return 0;
}


```
<hr>
<h3>Implementation using Adj list & vector</h3>





