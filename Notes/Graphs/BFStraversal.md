<h1>BFS Traversal in Graphs</h1>
<ul>
  <li>BFS ---> Breadth-first search</li>
  <li>Similar to BFT of trees, in which all the nodes at a particular level are printed first.</li>
  <li>The only difference b/w BFS of trees and Graphs is that Graphs may contain loops.</li>
  <li>To keep a track of loops, a bool variable will be initialized (Visited or Not visited).</li>

</ul>
<h3>Working of algorithm</h3>
<ul>
  <li>Requirements -> 
    <ol>
      <li>Visited Array: It will keep track, if the node is already visited or not</li>
      <li>Queue: All nodes at a particular level will be pushed in it. It is used as it has FIFO feature.</li> 
    </ol> 
  </li>
  <li>Follow five steps:
    <ol>
      <li>Source Node ko store karo</li>
      <li>Queue me push kardo</li>
      <li>Visited array me true mark krdo</li>
      <li>Queue se node ko pop krdo or uska data print krdo</li>
      <li>Us node ke saare neighbour ko queue me daaldo</li> 
    </ol>
  </li>
</ul>











