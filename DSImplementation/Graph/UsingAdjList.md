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
</ul>
<h5>Using Adj List & Unordered Map:</h5>
<ol>
  <li>Graph is represented by showing each node and all links of that node.<br>
<i>(Har node par jao, or btao ki kis kis node se connected hai, ye puri mapping ek graph ko represent kregi)</i></li>
  <li>unordered_map&lt;int, list&lt;int&gt;&gt; <br>
    first (int) -> Value of node, <br>
    second (list) -> list of all the node with which first node is linked</li>
</ol>
<code>
</code>
