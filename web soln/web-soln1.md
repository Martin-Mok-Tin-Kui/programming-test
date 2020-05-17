Soln for Question 1:  
For question 1, I choose to use an adjacency list to represent the undirected graph.  
Below are some major benefits for using this data structure representation in path finding algorithm:  
getting all nodes adjacent to node i takes O(1) steps.  
the neighbors of each vertex may be listed efficiently, in time proportional to the degree of the vertex.  

Adjacency list is usually implemented by linked list, but since javascript doesn’t have built in support for it, 
I choose to use ES6 set and map, so that the operations can be optimized by the javascript engine in the browser.  

As it is easier to manipulate integer, I will map the alphabet graph labeling scheme to integer labeling.
I used an array to map the index to the alphabet. So once I find the path I can display it back to letter.
e.g. 1->5->0 can be displayed to letter path by letter[1]->letter[5]->letter[0]
```js
const letter=['A','B','C','D','E','F','G','H'];
const adjacencyList = new Map();
adjacencyList.set(0, new Set([1,3,7]));
adjacencyList.set(1, new Set([0,2,3]));
adjacencyList.set(2, new Set([1,3,5]));
adjacencyList.set(3, new Set([0,2,4]));
adjacencyList.set(4, new Set([3,5,7]));
adjacencyList.set(5, new Set([2,4,6]));
adjacencyList.set(6, new Set([5,7]));
adjacencyList.set(7, new Set([0,6]));
```

1.1 To find all the paths from source node s to destination node d,
I use recursive Depth-first search (DFS) without the need to use stack, and print the result immediately once I found the path.

```js
const visited = new Set();
const dfs = node => {
  visit(node);
  visited.add(node);
  for (let neighbour of adjacencyList.get(node)) {
    if (!visited.has(neighbour)) {
     dfs(neighbour);
    }
  }
};
```
Reference:  
1.[Data Structures in JavaScript: Graphs](https://medium.com/better-programming/basic-interview-data-structures-in-javascript-graphs-3f9118aeb078)  
