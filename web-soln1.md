Question 1:  
For question 1, I choose to use an adjacency list to represent the undirected graph.  
Below are some major benefits for using this data structure representation in path finding algorithm:  
getting all nodes adjacent to node i takes O(1) steps.  
the neighbors of each vertex may be listed efficiently, in time proportional to the degree of the vertex.  

Adjacency list is usually implemented by linked list, but since javascript doesn’t have built in support for it, 
I choose to use ES6 set and map, so that the operations can be optimized by the javascript engine in the browser.  
'''js
const adjacencyList = new Map();
adjacencyList.set(1, new Set([2,3]));
adjacencyList.set(2, new Set([3,4]));
adjacencyList.set(3, new Set());
adjacencyList.set(4, new Set([3]));
'''

1.1 To find all the path from source node s to destination node d,
I use Depth-first search (DFS), so that I can print the result immediately once I found the path.

Reference:  
1.[Data Structures in JavaScript: Graphs](https://medium.com/better-programming/basic-interview-data-structures-in-javascript-graphs-3f9118aeb078)  
