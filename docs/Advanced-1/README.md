## Graph Theory

`Graph`  is probably the data structure that has the closest resemblance to our daily life. There are many types of graphs describing the relationships in real life. For instance, our friend circle is a huge “graph”.

![](https://assets.leetcode.com/static_assets/explore/The_basic_of_graph_1.png)

Figure 1. An example of a undirected graph.

In Figure 1 above, we can see that person G, B, and E are all direct friends of A, while person C, D, and F are indirect friends of A. This example is a social graph of friendship. So, what is the “graph” data structure?

## Types of “graphs”

There are many types of “graphs”. In this Explore Card, we will introduce three types of graphs:  **undirected graphs, directed graphs, and weighted graphs.**

### Undirected graphs

The edges between any two vertices in an “undirected graph” do not have a direction, indicating a two-way relationship.

Figure 1 is an example of an undirected graph.

### Directed graphs

The edges between any two vertices in a “directed graph” graph are directional.

Figure 2 is an example of a directed graph.

![](https://assets.leetcode.com/static_assets/explore/The_basic_of_graph_2.png)

Figure 2. An example of a directed graph.

### Weighted graphs

Each edge in a “weighted graph” has an associated weight. The weight can be of any metric, such as time, distance, size, etc. The most commonly seen “weighted map” in our daily life might be a city map. In Figure 3, each edge is marked with the distance, which can be regarded as the weight of that edge.

![](https://assets.leetcode.com/static_assets/explore/The_basic_of_graph_3.png)

Figure 3. An example of a weighted graph.

## The Definition of “graph” and Terminologies

“Graph” is a non-linear data structure consisting of vertices and edges. There are a lot of terminologies to describe a graph. If you encounter an unfamiliar term in the following Explore Card, you may look up the definition below.

-   Vertex: In Figure 1, nodes such as A, B, and C are called vertices of the graph.
-   Edge: The connection between two vertices are the edges of the graph. In Figure 1, the connection between person A and B is an edge of the graph.
-   Path: the sequence of vertices to go through from one vertex to another. In Figure 1, a path from A to C is [A, B, C], or [A, G, B, C], or [A, E, F, D, B, C].
    
    **Note**: there can be multiple paths between two vertices.
    
-   Path Length: the number of edges in a path. In Figure 1, the path lengths from person A to C are 2, 3, and 5, respectively.
-   Cycle: a path where the starting point and endpoint are the same vertex. In Figure 1, [A, B, D, F, E] forms a cycle. Similarly, [A, G, B] forms another cycle.
-   Negative Weight Cycle: In a “weighted graph”, if the sum of the weights of all edges of a cycle is a negative value, it is a negative weight cycle. In Figure 4, the sum of weights is -3.
-   Connectivity: if there exists at least one path between two vertices, these two vertices are connected. In Figure 1, A and C are connected because there is at least one path connecting them.
-   Degree of a Vertex: the term “degree” applies to unweighted graphs. The degree of a vertex is the number of edges connecting the vertex. In Figure 1, the degree of vertex A is 3 because three edges are connecting it.
-   In-Degree: “in-degree” is a concept in directed graphs. If the in-degree of a vertex is d, there are d directional edges incident to the vertex. In Figure 2, A’s indegree is 1, i.e., the edge from F to A.
-   Out-Degree: “out-degree” is a concept in directed graphs. If the out-degree of a vertex is d, there are d edges incident from the vertex. In Figure 2, A’s outdegree is 3, i,e, the edges A to B, A to C, and A to G.

![](https://assets.leetcode.com/static_assets/explore/4._Negative_Cycle.png)

Figure 4. An example of a negative weight cycle.

## Representations of Graph

Here are the two most common ways to represent a graph :

1.  Adjacency Matrix
2.  Adjacency List

### Adjacency Matrix

An adjacency matrix is a way of representing a graph as a matrix of boolean (0’s and 1’s).

Let’s assume there are ****n**** vertices in the graph So, create a 2D matrix ****adjMat[n][n]**** having dimension n x n.
> -   If there is an edge from vertex ****i**** to ****j****, mark ****adjMat[i][j]**** as ****1****.
> -   If there is no edge from vertex ****i**** to ****j****, mark ****adjMat[i][j]**** as ****0****.

### Representation of Undirected Graph to Adjacency Matrix:

The below figure shows an undirected graph. Initially, the entire Matrix is ​​initialized to ****0****. If there is an edge from source to destination, we insert ****1**** to both cases (****adjMat[destination]**** and ****adjMat****[****destination])**** because we can go either way.

![Undirected_to_Adjacency_matrix](https://media.geeksforgeeks.org/wp-content/uploads/20230727130331/Undirected_to_Adjacency_matrix.png)


### Representation of Directed Graph to Adjacency Matrix:

The below figure shows a directed graph. Initially, the entire Matrix is ​​initialized to ****0****. If there is an edge from source to destination, we insert ****1**** for that particular ****adjMat[destination]****.

![Directed_to_Adjacency_matrix](https://media.geeksforgeeks.org/wp-content/uploads/20230727130528/Directed_to_Adjacency_matrix.png)



### Adjacency List

An array of Lists is used to store edges between two vertices. The size of array is equal to the number of ****vertices (i.e, n)****. Each index in this array represents a specific vertex in the graph. The entry at the index i of the array contains a linked list containing the vertices that are adjacent to vertex ****i****.

Let’s assume there are ****n**** vertices in the graph So, create an ****array of list**** of size ****n**** as ****adjList[n].****

> -   adjList[0] will have all the nodes which are connected (neighbour) to vertex ****0****.
> -   adjList[1] will have all the nodes which are connected (neighbour) to vertex ****1**** and so on.

### Representation of Undirected Graph to Adjacency list:

The below undirected graph has 3 vertices. So, an array of list will be created of size 3, where each indices represent the vertices. Now, vertex 0 has two neighbours (i.e, 1 and 2). So, insert vertex 1 and 2 at indices 0 of array. Similarly, For vertex 1, it has two neighbour (i.e, 2 and 1) So, insert vertices 2 and 1 at indices 1 of array. Similarly, for vertex 2, insert its neighbours in array of list.

![Graph-Representation-of-Undirected-graph-to-Adjacency-List](https://media.geeksforgeeks.org/wp-content/uploads/20230727154843/Graph-Representation-of-Undirected-graph-to-Adjacency-List.png)


### Representation of Directed Graph to Adjacency list:

The below directed graph has 3 vertices. So, an array of list will be created of size 3, where each indices represent the vertices. Now, vertex 0 has no neighbours. For vertex 1, it has two neighbour (i.e, 0 and 2) So, insert vertices 0 and 2 at indices 1 of array. Similarly, for vertex 2, insert its neighbours in array of list.

![Graph-Representation-of-Directed-graph-to-Adjacency-List](https://media.geeksforgeeks.org/wp-content/uploads/20230727155209/Graph-Representation-of-Directed-graph-to-Adjacency-List.png)


## Common algorithms

### BFS:
Breadth-first search (BFS) is an algorithm for searching a tree data structure for a node that satisfies a given property. It starts at the tree root and explores all nodes at the present depth prior to moving on to the nodes at the next depth level. Extra memory, usually a queue, is needed to keep track of the child nodes that were encountered but not yet explored.  

BFS is actually traversing the nodes level by level. That is, traversing the node first, then its children and then its children’s children. If you consider the following tree,

![image](https://assets.leetcode.com/users/images/6213c7b8-9f06-48f6-bb50-d10b37070957_1613720241.0043335.png)

The root node is A. Its left and right children are  **B**  and  **C**. Further its children are  **D,E,F**  and  **G**. So the  **BFS**  of the above tree is

```
          ABCDEFG

```

Here  **Level Order traversal**  of a tree is going to be same as  **BFS**  since it traverse starting from level 0 till its last level. But not every BFS is level order traversal. For example,

![image](https://assets.leetcode.com/users/images/cd2e1cde-2d41-4a9d-b42e-e91d27bbee6c_1613720439.3248208.png)

Here the  **BFS**  traverse its left and right children first and then its children.

So the BFS traversal of the above tree is  **12345**. Whereas Level Order traverse level by level. So the level order traversal of the same tree is  **13245**.

Traversing the graph in BFS way is again going to be same. That visiting the nodes wider as the graph goes.  
Consider the following graph,

![image](https://assets.leetcode.com/users/images/e40b66e6-ba34-4d17-8bf6-d36bff715b45_1613720607.019259.png)

Let’s traverse starting from Node  **0**, we first visit  **0**  and traversing its neighbouring nodes  **1**  and  **2**.

![image](https://assets.leetcode.com/users/images/c94c8e8b-99b9-4a38-9a3c-034ee79e940f_1613720659.8195944.png)

![image](https://assets.leetcode.com/users/images/ff400e98-7fed-48c4-99a1-3cab5375d137_1613720696.1264007.png)

Further traversing the next wider level  **2**  and  **5**. And Finally  **4**.

![image](https://assets.leetcode.com/users/images/59b36465-bae4-41e6-af2f-9933489a28dd_1613720854.9190488.png)

![image](https://assets.leetcode.com/users/images/3a367ac3-d1e6-4f7c-a57e-57466667a550_1613720875.3771782.png)

**Implementation:**  
**BFS: FIFO (First In First Out)**  
In Breadth-First-Search,  **queue**  is going to be our hero. Here are the steps to implement BFS programmatically.

1.  Put the visited node in queue.
2.  Explore its children, add them to queue, and remove the visited node.
3.  Visit all the nodes until queue becomes empty.

![image](https://assets.leetcode.com/users/images/b0c246b4-7228-4737-84ac-96930750bb52_1613721366.2659638.png)

In the above tree,

1.  we first put the root node  **A**  in queue.  **A**’s children are  **B**  and  **C**. Add them to queue and remove  **A**.
2.  Further pull  **B**, add its children  **D**  and  **E**  to queue and remove  **B**.
3.  Pull  **C**, add its children  **F**  and  **G**  to queue and remove  **C**.
4.  **D,E,F**  and  **G**  have no children, so pop them from queue.


### [Question](https://github.com/doocs/leetcode/blob/main/solution/1700-1799/1730.Shortest%20Path%20to%20Get%20Food/README_EN.md) : Shortest path to food
**Description**

You are starving and you want to eat food as quickly as possible. You want to find the shortest path to arrive at any food cell.

You are given an  `m x n`  character matrix,  `grid`, of these different types of cells:

-   `'*'`  is your location. There is  **exactly one** `'*'`  cell.
-   `'#'`  is a food cell. There may be  **multiple**  food cells.
-   `'O'`  is free space, and you can travel through these cells.
-   `'X'`  is an obstacle, and you cannot travel through these cells.

You can travel to any adjacent cell north, east, south, or west of your current location if there is not an obstacle.

Return  _the  **length**  of the shortest path for you to reach  **any**  food cell_. If there is no path for you to reach food, return  `-1`.

**Example 1:**

[![](https://camo.githubusercontent.com/56a064b341f99868d79208264b3742d59cc23fe26178d12a1a9fd80d2e5532c6/68747470733a2f2f666173746c792e6a7364656c6976722e6e65742f67682f646f6f63732f6c656574636f6465406d61696e2f736f6c7574696f6e2f313730302d313739392f313733302e53686f727465737425323050617468253230746f253230476574253230466f6f642f696d616765732f696d67312e6a7067)](https://camo.githubusercontent.com/56a064b341f99868d79208264b3742d59cc23fe26178d12a1a9fd80d2e5532c6/68747470733a2f2f666173746c792e6a7364656c6976722e6e65742f67682f646f6f63732f6c656574636f6465406d61696e2f736f6c7574696f6e2f313730302d313739392f313733302e53686f727465737425323050617468253230746f253230476574253230466f6f642f696d616765732f696d67312e6a7067)

**Input:** grid = [["X","X","X","X","X","X"],["X","*","O","O","O","X"],["X","O","O","#","O","X"],["X","X","X","X","X","X"]]
**Output:** 3
**Explanation:** It takes 3 steps to reach the food.

**Example 2:**

[![](https://camo.githubusercontent.com/25f96060c8da5aba132e82707f60efd19a4f3b5201fd3648f4e011e26e3127a3/68747470733a2f2f666173746c792e6a7364656c6976722e6e65742f67682f646f6f63732f6c656574636f6465406d61696e2f736f6c7574696f6e2f313730302d313739392f313733302e53686f727465737425323050617468253230746f253230476574253230466f6f642f696d616765732f696d67322e6a7067)](https://camo.githubusercontent.com/25f96060c8da5aba132e82707f60efd19a4f3b5201fd3648f4e011e26e3127a3/68747470733a2f2f666173746c792e6a7364656c6976722e6e65742f67682f646f6f63732f6c656574636f6465406d61696e2f736f6c7574696f6e2f313730302d313739392f313733302e53686f727465737425323050617468253230746f253230476574253230466f6f642f696d616765732f696d67322e6a7067)

**Input:** grid = [["X","X","X","X","X"],["X","*","X","O","X"],["X","O","X","#","X"],["X","X","X","X","X"]]
**Output:** -1
**Explanation:** It is not possible to reach the food.

**Example 3:**

[![](https://camo.githubusercontent.com/94a7554ef5e2a7f877d39949e24c238e0c0e4be33714d2b39289df3a71176793/68747470733a2f2f666173746c792e6a7364656c6976722e6e65742f67682f646f6f63732f6c656574636f6465406d61696e2f736f6c7574696f6e2f313730302d313739392f313733302e53686f727465737425323050617468253230746f253230476574253230466f6f642f696d616765732f696d67332e6a7067)](https://camo.githubusercontent.com/94a7554ef5e2a7f877d39949e24c238e0c0e4be33714d2b39289df3a71176793/68747470733a2f2f666173746c792e6a7364656c6976722e6e65742f67682f646f6f63732f6c656574636f6465406d61696e2f736f6c7574696f6e2f313730302d313739392f313733302e53686f727465737425323050617468253230746f253230476574253230466f6f642f696d616765732f696d67332e6a7067)

**Input:** grid = [["X","X","X","X","X","X","X","X"],["X","*","O","X","O","#","O","X"],["X","O","O","X","O","O","X","X"],["X","O","O","O","O","#","O","X"],["X","X","X","X","X","X","X","X"]]
**Output:** 6
**Explanation:** There can be multiple food cells. It only takes 6 steps to reach the bottom food.

**Constraints:**

-   `m == grid.length`
-   `n == grid[i].length`
-   `1 <= m, n <= 200`
-   `grid[row][col]`  is  `'*'`,  `'X'`,  `'O'`, or  `'#'`.
-   The  `grid`  contains  **exactly one**  `'*'`.

**Solution**

```python
class Solution:
    def getFood(self, grid: List[List[str]]) -> int:
        m, n = len(grid), len(grid[0])
        i, j = next((i, j) for i in range(m) for j in range(n) if grid[i][j] == '*')
        q = deque([(i, j)])
        dirs = (-1, 0, 1, 0, -1)
        ans = 0
        while q:
            ans += 1
            for _ in range(len(q)):
                i, j = q.popleft()
                for a, b in pairwise(dirs):
                    x, y = i + a, j + b
                    if 0 <= x < m and 0 <= y < n:
                        if grid[x][y] == '#':
                            return ans
                        if grid[x][y] == 'O':
                            grid[x][y] = 'X'
                            q.append((x, y))
        return -1

```
**Notes**:
![image](https://assets.leetcode.com/users/images/459f610d-8108-4803-8188-e2312a0a70cd_1648525376.9628026.png)  
Visualization of BFS with first 3 layers. A - root node/first lavel, C/M/B/O - second layer, D/N/L/J - third layer.  

1.  Algorithm uses queue for implementation.
2.  It checks whether a vertex has been explored before enqueueing the vertex.
3.  We can track if the node was already explored by modifying the original matrix.
4.  BFS algorithm can be instructed with additional array dist which can help to  
    track the parent node of the next node. This will help to reconstruct the path  
    by looping backward from end node.

### DFS:
Is an algorithm for traversing or searching tree or graph data structures. The algorithm starts at the root node (selecting some arbitrary node as the root node in the case of a graph) and explores as far as possible along each branch before backtracking.

As BFS traverse wide, DFS goes deep. It starts from first node, and goes deep in a path till it traverse the leaf node/the last node before start traversing its next path.

![image](https://assets.leetcode.com/users/images/cfb07711-ceb2-44c3-978f-01255758b32b_1613720946.4616702.png)

In the above tree, it first starts from root node  **1**, does deep to  **2**  and more deeper to  **4**. Node  **4**  has no children, so it is done with that path visits  **5**  and traverse back to  **1**  and starts visiting deep  **3,6**  and  **7**.

Further we can traverse in three different ways,

1.  **Pre-Order:**  Visiting  **root**  first,  **left**  node next and finally  **right**  node.
2.  **Inorder:**  Visiting  **left**  first,  **root**  node next and finally  **right**  node.
3.  **Post-Order:**  Visiting  **left**  first,  **right**  node next and finally  **root**  node.

So the traversal of above tree is going to be,

```
Pre-Order: 1245367
Inorder: 4251637
Post-Order: 4526731

```

DFS of graph is also goes  **deep**  till it traverse all the nodes in the graph.

![image](https://assets.leetcode.com/users/images/b5fcadc9-208e-45f6-879f-e3db861541c9_1613721257.0779736.png)

**Implementation:**
**DFS: LIFO (Last In First Out)**  
We are going to get the help of  **stack**, in order to traverse the tree/graph DFS way.

1.  Add the visited Node to stack.
2.  Pop the Node from stack, explore its children and add them to stack.
3.  Explore all the nodes till stack becomes empty.  
    Here we are going to see pre-order traversal of the below tree using stack. Same technique can be used to perform both inorder and post-order traversals just by changing the order of visiting nodes.

![image](https://assets.leetcode.com/users/images/2132f541-ed91-42a3-a6ba-e33052cb4488_1613721512.2723231.png)

### [Question](https://leetcode.com/problems/keys-and-rooms/): Keys and Rooms
**Description**
There are  `n`  rooms labeled from  `0`  to  `n - 1` and all the rooms are locked except for room  `0`. Your goal is to visit all the rooms. However, you cannot enter a locked room without having its key.

When you visit a room, you may find a set of  **distinct keys**  in it. Each key has a number on it, denoting which room it unlocks, and you can take all of them with you to unlock the other rooms.

Given an array  `rooms`  where  `rooms[i]`  is the set of keys that you can obtain if you visited room  `i`, return  `true`  _if you can visit  **all**  the rooms, or_  `false`  _otherwise_.

**Example 1:**

**Input:** rooms = [[1],[2],[3],[]]
**Output:** true
**Explanation:** 
We visit room 0 and pick up key 1.
We then visit room 1 and pick up key 2.
We then visit room 2 and pick up key 3.
We then visit room 3.
Since we were able to visit every room, we return true.

**Example 2:**

**Input:** rooms = [[1,3],[3,0,1],[2],[0]]
**Output:** false
**Explanation:** We can not enter room number 2 since the only key that unlocks it is in that room.

**Constraints:**

-   `n == rooms.length`
-   `2 <= n <= 1000`
-   `0 <= rooms[i].length <= 1000`
-   `1 <= sum(rooms[i].length) <= 3000`
-   `0 <= rooms[i][j] < n`
-   All the values of  `rooms[i]`  are  **unique**.
In above example,

1.  First we are visiting Node  **1**, add them to stack, explore its children and add its right child  **3**  first and then left child  **2**.
2.  Now the stack has nodes  **2**  and  **3**. Explore  **2**’s children and add its right child  **5**  and then its left child  **4**  to stack. And pop  **2**.
3.  Further pop nodes from stack and add its children until stack becomes empty.

**Solution**
-   The basic idea of the code is to keep a record of all the keys you have already obtained.
-   You can obtain all the keys in the rooms that you can go to
-   And if the count of all the keys you can obtain is equal to the number of rooms, your answer is True.

**Code**

```python
class Solution:
    def canVisitAllRooms(self, rooms: List[List[int]]) -> bool:
        
        res = set() #set of keys that we can obtain
        visited = set() #set of rooms we have visited

        n = len(rooms)

        def solve(pos):
            if pos in visited:
                return

            visited.add(pos)
            temp = rooms[pos]
            for i in temp:
                res.add(i)
                solve(i)

        solve(0)
        if 0 in res:
            res.remove(0)

        return len(res) == n - 1
```
**Notes**:

1.  Algorithm usually uses recursion implementation.
2.  We mark the node as visited and will keep exploring its neighbors if there are not yet explored.
3.  DFS can be useful to find connected components. We can iterate through the nodes and call dfs() to find all nodes which belongs to component.
4.  We can use unordered_map<int, vector> to represent the graph.

### Minimum Spanning Tree (Prim's Algorithm):
Minimum Spanning Tree (MST) is a spanning tree with  **least possible edge weight**. What that means is that it is an undirected graph, where all the vertices are connected, with least possible edge weight, and no cycles. A weighted, undirected, and connected graph can have many spanning trees but  **only one**  MST.

Here is an image of a weighted, undirected, and connected graph. Blue edges are all the spanning trees of this graph and  **red edges are the minimum spanning tree**  (We will only use MST for all the future explanations in this guide.)

![image](https://assets.leetcode.com/users/images/f8c9bef6-57b5-452d-bf56-813f3ae638a5_1616967620.6859152.png)

The total number of vertices, V in this Graph are 6. The total number of edges, E in an MST is  **(V-1)**  i.e. 6-1=5 edges. This is what the MST looks like for the above graph-

![image](https://assets.leetcode.com/users/images/2273c26f-bc41-49da-9660-c154704a4dc3_1616967755.0905151.png)

Alright, now that we have a basic understanding of how MST is supposed to be, let’s try and understand how to find a minimum spanning tree when given a graph!

**Prim's Algorithm**  
Prim’s algorithm is a greedy algorithm. To find the MST using Prim’s, we pick an initial starting vertex and add it to a set. Then we grow the MST from that initial vertex by adding adjacent vertices one by one based on least value of edge weight.

Let’s create 2 disjoint (no common value) subsets of vertices, one is called StartSet and the other is called MstSet. StartSet is a key value pair with vertices and their distances from the adjacent vertix that has been added to the MstSet.  
In the beginning, StartSet has all the vertices and MstSet has nothing.

```
StartSet: {(A, INF), (B, INF), (C, INF), (D, INF), (E, INF), (F, INF)}
MstSet: {}

```

Let’s pick a starting point. It doesn’t matter which one because MST is unique and no matter where you start, you are going to end up with the same tree.

I will begin at vertex C. From vertex C, we have the following paths-  
![image](https://assets.leetcode.com/users/images/4741f613-eeed-4385-bead-b886303b5301_1616968241.0673938.png)

Since we picked our starting point, let's add vertex C to MstSet and update it's value to 0 in StartSet (as it is our initial vertex and distant from a node to itself is 0.  
Also update the values of vertices adjacent to C with their distances from C. Since A, D and E are adjacent to C, their values in StartSet are updated. Our subsets look as follows-

```
StartSet: {(A, 7), (B, INF), (C, 0), (D, 2), (E, 3), (F, INF)}
MstSet: {C}

```

From C, we can either pick A, D, or E as our next vertex.  
Since the Prim's algorithm is Greedy, it will choose the path of least value i.e. the edge between C and D and will add vertex D to MstSet.  
![image](https://assets.leetcode.com/users/images/53d1882b-4c4a-46d4-a704-de8658a9e715_1616968241.122233.png)  
Next, the same process repeats with D. Update the value of vertices adjacent to D in StartSet. One thing to note here is that the distance of A from D is 6 which is less than distance of A from C. Therefore, in our subset StartSet, the value of A will update to 6 from 7. Same goes for E whose value will be updated from 3 to 1.  
Let's look at the values in our subsets-

```
StartSet: {(A, 6), (B, 7), (C, 0), (D, 2), (E, 1), (F, INF)}
MstSet: {C, D}

```

So far we have C and D in our MST. Let's grow our MST some more by picking the next vertex.

Now our edge values are 6, 7 and 1. Since 1 is smallest, the next vertex to be added to the MstSet will be E. You can also look at our subsets and see that out of all the vertices that are currently not in MstSet, E has the least value.  
![image](https://assets.leetcode.com/users/images/3beebdeb-f544-48b9-9eeb-bb66b9203d7c_1616968241.0846808.png)  
Continuing our tradition of updating adjacent vertices in StartSet, B is updated to 5 and F is updated to 4.  
Our subsets currently look like this-

```
StartSet: {(A, 6), (B, 5), (C, 0), (D, 2), (E, 1), (F, 4)}
MstSet: {C, D, E}

```

Now we may have a problem! The values of edges coming from E are 3, 4 and 5. Since 3 is smaller than the 2, ideally we should pick that. However, we can't do that because C is already in MstSet. So we will go a step further and pick the edge with value 4 i.e. the E-F edge.  
Once again, add F to MstSet and update the adjacent vertices' values.  
![image](https://assets.leetcode.com/users/images/5372e4c4-ec23-4736-bc8d-fe33e31b0c1e_1616968241.1647825.png)

There is no change of values for vertices adjacent to F.  
Let's take a quick look at our subsets after adding F.

```
StartSet: {(A, 6), (B, 5), (C, 0), (D, 2), (E, 1), (F, 4)}
MstSet: {C, D, E, F}

```

Now the only vertices that are not in MstSet are A and B. As you can see from the subset, between A and B, B has the smaller value (5). Also in the graph, the least value of edge weight to reach B is 5 (E-B edge) as compared to A which is 7 (F-A edge).

Therefore, we will go ahead and add B to our MstSet and update the values of it's adjacent vertices.  
Value of A is updated to 3.  
Our subsets look like this-

```
StartSet: {(A, 3), (B, 5), (C, 0), (D, 2), (E, 1), (F, 4)}
MstSet: {C, D, E, F, B}

```

Now, only A needs to be added. As we can see from both the graph and the subset, the least cost way to reach A is through A-B edge.  
![image](https://assets.leetcode.com/users/images/6793ff5d-6736-4cd5-aa49-d6e97b4058ea_1616968241.3497143.png)  
So, we will add A to our MstSet.  
Let's look at the final values of our subsets-

```
StartSet: {(A, 3), (B, 5), (C, 0), (D, 2), (E, 1), (F, 4)}
MstSet: {C, D, E, F, B, A}

```

All the vertices have been added to the MstSet!  
And finally, we have our Minimum Spanning Tree.  
![image](https://assets.leetcode.com/users/images/2c3826ff-3b77-44ea-867b-14a178321d2d_1616968241.1259313.png)

### [Question](https://github.com/azl397985856/leetcode/blob/master/problems/1168.optimize-water-distribution-in-a-village-en.md): Optimized water distribution in a village
**Description**

There are n houses in a village. We want to supply water for all the houses by building wells and laying pipes.

For each house i, we can either build a well inside it directly with cost wells[i], or pipe in water from another well to it. The costs to lay pipes between houses are given by the array pipes, where each pipes[i] = [house1, house2, cost] represents the cost to connect house1 and house2 together using a pipe. Connections are bidirectional.

Find the minimum total cost to supply water to all houses.

**Example 1:**

**Input:** n = 3, wells = [1,2,2], pipes = [[1,2,1],[2,3,1]]
**Output:** 3
**Explanation:** 
The image shows the costs of connecting houses using pipes.
The best strategy is to build a well in the first house with cost 1 and connect the other houses to it with cost 2 so the total cost is 3.

**Constraints:**

 - 1 <= n <= 10000 
 - wells.length == n 
 - 0 <= wells[i] <= 10^5 
 - 1 <= pipes.length <= 10000 
 - 1 <= pipes[i][0], pipes[i][1] <= n 
 - 0 <= pipes[i][2] <= 10^5 
 - pipes[i][0] != pipes[i][1] 

example 1 pic:

[![example 1](https://camo.githubusercontent.com/8370f44739d5a49b9e660395388706b734e13a23b42bd792f893b1930bfa2fcc/68747470733a2f2f702e697069632e7669702f7838626230342e6a7067)](https://camo.githubusercontent.com/8370f44739d5a49b9e660395388706b734e13a23b42bd792f893b1930bfa2fcc/68747470733a2f2f702e697069632e7669702f7838626230342e6a7067)

**Code**

```python
import heapq
import collections
def minCostToSupplyWater(n, wells, pipes):
    c = collections.defaultdict(list)
    for i, cost in enumerate(wells, 1):
        c[0].append((cost, i))
        c[i].append((cost, 0))
    for i, j, cost in pipes:
        c[i].append((cost, j))
        c[j].append((cost, i))
    
    cnt, ans, visited, heap = 1, 0, [0] * (n+1), c[0]
    visited[0] = 1
    heapq.heapify(heap)
    while heap:
        d, j = heapq.heappop(heap)
        if not visited[j]:
            visited[j], cnt, ans = 1, cnt+1, ans+d
            for record in c[j]: heapq.heappush(heap, record)    
    return ans
```
### Dijkstra's algorithm:
Is an algorithm for finding the shortest paths between nodes in a graph, which may represent, for example, road networks.

Dijkstra's algorithm is a  **Single-Source-Shortest-Path algorithm**, which means that it calculates shortest distance from one vertex to all the other vertices.

The node from where we want to find the shortest distance is known as the  **source node**. For the rest of the tutorial, I'll always label the source node as  **S**. And the distance to source node is naturally going to be  **zero**.

```
So, if we had an array of distances called dist[] and source node is 2 then dist[] would be 
[INF, INF, 0, INF, INF]	
  0    1   2   3    4
// Consider INF as infinity since we don't know what the actual distance is. But we are very much sure that the distance to the source node is 0.

```

Let's start.

Have a look at the image below. We shall work with it in this tutorial.  
![image](https://assets.leetcode.com/users/images/3cfb95be-11e6-4a61-8c54-397388698f9f_1612973716.479781.png)

Remember what I said about the source node? I said that we were  **SURE**  that the shortest distance to source node is going to be zero. Do you agree with me on that point? Of course, yes, because there was no path to travel.

What does the distance array for our graph look like?

```
Node 	 |  S   A   B   C   D 
Distance |  0  INF INF INF INF

```

Let's break the problem. Let's rip apart this graph.

We are at S currently. Let's see where we can go from S.  
![image](https://assets.leetcode.com/users/images/6746ae95-91de-4705-812f-8451c56a2bb8_1612973800.0847409.png)

You are at node S. There are 2 edges that come out of S. One edge goes to A and other goes to B. Edge SA distance is 15 and edge SB distance if 10. You can clearly verify this in the figure.

I now claim that I am SURE that the shortest distance to B is 10. Why though? How many other ways are possible, through which you can reach to node B? Maybe there will be some edge from A to B. But since distance to A is already 15, any edge from A to B will only increase that distance and will never be able to become less than 10. This is the most important step. Read it again if you did not get it.

Now, that I am SURE of the shortest distance to reach B, I discover more vertices from B.

Now, our exploration graph looks something like this.  
![image](https://assets.leetcode.com/users/images/374e1c43-bff9-47d0-b453-1c5d9daf94e4_1612973846.186549.png)  
and the distance array has been updated.

```
Node 	 |  S   A   B   C   D 
Distance |  0  INF  10 INF INF

```

Let's see what the current scenario looks like.

Nodes for which we know the shortest distance: S and B.

What are we looking at now?

At all the nodes we can reach from the S and B.

Again, the same question. Which node's shortest distance can we be SURE of ?

I claim it's node D.  
Look at the figure again.  
![image](https://assets.leetcode.com/users/images/08f2557a-7db6-406d-b7c6-8963c32dcfa9_1612973908.7902455.png)  
The distance to D is 10 + 1 = 11, and no other path can have length smaller than this since their own distances are greater than 11.

Hence, we now include D in our set of vertices for which shortest distances is known. Also, we explore more edges going from node D.

Note that we are always picking the green vertex with the minimum distance.

So, now our exploration graph looks something like this.

![image](https://assets.leetcode.com/users/images/7d57800a-5fdc-4242-8877-66322ca709ba_1612973944.6547043.png)  
Distance has been updated.

```
Node 	 |  S   A   B   C   D 
Distance |  0  INF  10 INF  11

```

Now, same question. Which node's shortest distance can we be SURE of? More specifically. Which green node's shortest distance can we be SURE of? Yes, right. It is C because the path S-B-D-C gives distance of 10 + 1 + 3 = 14 which is the lowest.

Hence, we include C into the set of nodes for which final distance have been finalized and we also explore it's neighbours.

The exploration graph now looks like this.  
![image](https://assets.leetcode.com/users/images/6a64e3aa-dada-4c56-be5f-fc15c7bcd429_1612973987.8125973.png)  
Distance has been updated again.

```
Node 	 |  S   A   B   C   D 
Distance |  0  INF  10  14  11

```

Again, for which node are we SURE of? There is just one node remaining and so it is the shortest. So, we include it in the set of nodes whose final distances are known and explore it's neighbours.

Now, the exploration graph is as follows:  
![image](https://assets.leetcode.com/users/images/50fe5e41-a2a2-4085-a22a-6d724a111559_1612974049.2119877.png)

Final distance array now looks like this:

```
Node 	 |  S   A   B   C   D 
Distance |  0  15  10  14  11

```

But now, since we have no green nodes, we stop. We have visited all the nodes.

Couple of key points here. How were we SURE of the shortest distance of a green node? That node had the shortest distance among all the other green nodes.

**Now, summarizing Djikstra's algorithm:**

1.  We keep a set of vertices for which final shortest distance is already known to us. Initially only the source vertex S belongs to this set.
2.  We do several iterations, during which we pick the green node with the minimum distance and add it to the set of vertices whose distances are finalized and also all nodes reaching from this node and not VISITED (i.e. NOT MARKED YELLOW), are made green.

And that's it. That's the working of Djikstra's algorithm.

Regarding the implementation, since we need the node with minimum distance, a min-heap is prefered. Implementations with sets( the ones based on BSTs) are also popular. You can find the implementations online with both the data structures.

Now, for a moment, let's go back to where we started.

![image](https://assets.leetcode.com/users/images/ff1bfecb-d267-4944-a55a-d00c0c37f5ba_1612974108.4932501.png)  
At this point, we chose B. So, what we have done is finalized the distance to B and it can never be changed in coming iterations. Now, let's say that there was an edge from A to B with cost as -10 (Negative ten). The distance then is 15 + (-10) = 5, which is lower than 10.

But, we had said that it can never be less than 10. Then, how come this?

Here is the truth. Djikstra's algorithm doesn't work for negative edge weights.

Let's think about the graphs involving negative weights cycles. If there is a negative weight cycle like the C-A-B-C below, we can keep moving in cycles and each iteration of the cycle will decrease the distance, so negative weight cycle is a big NO for Djikstra.  
![image](https://assets.leetcode.com/users/images/0eefe88c-4e66-4ad0-9032-0e20ca1fe2de_1612974143.5970755.png)  
It's intuitive to understand that Djikstra doesn't work for negative cycles but not very intuitive to understand why it doesn't work for negative edges with no negative cycles.

### [Question](https://leetcode.com/problems/network-delay-time/) : Network Delay Time

You are given a network of  `n`  nodes, labeled from  `1`  to  `n`. You are also given  `times`, a list of travel times as directed edges  `times[i] = (ui, vi, wi)`, where  `ui`  is the source node,  `vi`  is the target node, and  `wi`  is the time it takes for a signal to travel from source to target.

We will send a signal from a given node  `k`. Return  _the  **minimum**  time it takes for all the_  `n`  _nodes to receive the signal_. If it is impossible for all the  `n`  nodes to receive the signal, return  `-1`.

**Example 1:**

![](https://assets.leetcode.com/uploads/2019/05/23/931_example_1.png)

**Input:** times = [[2,1,1],[2,3,1],[3,4,1]], n = 4, k = 2
**Output:** 2

**Example 2:**

**Input:** times = [[1,2,1]], n = 2, k = 1
**Output:** 1

**Example 3:**

**Input:** times = [[1,2,1]], n = 2, k = 2
**Output:** -1

**Constraints:**

-   `1 <= k <= n <= 100`
-   `1 <= times.length <= 6000`
-   `times[i].length == 3`
-   `1 <= ui, vi <= n`
-   `ui != vi`
-   `0 <= wi <= 100`
-   All the pairs  `(ui, vi)`  are  **unique**. (i.e., no multiple edges.)

**Solution:**
```python
class Solution:
    def networkDelayTime(self, times: List[List[int]], n: int, k: int) -> int:
        #create adjacency list
        adjList = {i:[] for i in range(1, n+1)} #node: [neighbour, weight]
        for src, dest, weight in times:
            adjList[src].append([dest, weight])
        #create minHeap
        minHeap = []
        minHeap.append([0, k])
        heapq.heapify(minHeap)
        #dikjstra 
        dist = [float("inf")] * (n+1)
        dist[k] = 0
        while minHeap:
            dis, node = heapq.heappop(minHeap)
            for it in adjList[node]:
                edgeWeight = it[1]
                edgeNode = it[0]
                if (dis+edgeWeight) < dist[edgeNode]:
                    dist[edgeNode] = dis+edgeWeight
                    heapq.heappush(minHeap, [dist[edgeNode], edgeNode])
        #result
        return max(dist[1:]) if max(dist[1:]) != float("inf") else -1 
```
**Description**

![image](https://assets.leetcode.com/users/images/728062f8-be3e-407c-a010-64da141864ed_1648524882.3623493.png)  
Visualization of traversing graph using Dijkstra algorithm and distance array. The priority queue itself is not shown there, as well as redundant nodes that we might have in priority queue. Green node - explored/current node, Yellow - node in the priority queue.  
**Notes**:

1.  We will have a set to track visited nodes.
2.  We will create a distance array to track the distance to each node. Initial node will have 0, others maximum. There is a room for optimization: if the node we got from the pq has larger cost than in our dist[] array, we should not explore it as we already got a better option.
3.  We will use min priority_queue to get the node with the minimum distance from the current node.
4.  If we are only interested in shortes distance till some END node, we can terminate the search earlier: if (node == dst) return cost;
5.  If we already find a better path we shouldn't explore it further: if (dist[node] < stops) continue;

## Extra Graph Algorithms:

### Union-Find:
Union–find data structure or disjoint-set data structure or merge–find set, is a data structure that stores a collection of disjoint (non-overlapping) sets. Equivalently, it stores a partition of a set into disjoint subsets. It provides operations for adding new sets, merging sets (replacing them by their union), and finding a representative member of a set. Helps to find the number of connected components, and can help to find MST.

```
class UnionFind {
    public:
    UnionFind(int n) : parent(n) {
        iota(parent.begin(), parent.end(), 0);
    }

    int Find(int x) {
        int temp = x;
        while (temp != parent[temp]) {
            temp = parent[temp];
        }
		// Path compression below
        while (x != temp) {
            int next = parent[x];
            parent[x] = temp;
            x = next;
        }
        return x;
    }

    void Union(int x, int y) {
        int xx = Find(x);
        int yy = Find(y);
        if (xx != yy) {
            parent[xx] = yy;
        }
    }

    private:
           vector<int> parent;
};

```

![image](https://assets.leetcode.com/users/images/1928b46b-6191-4858-879e-4a28c5857646_1648524550.5650837.png)  
The above picture demonstrates the state of the parent array after multiple Union() calls, follows multiple Find() calls.  
**Notes**:  
1. We can use vector to hold the set of nodes or unordered_map<int, int> if we don't know the amount of nodes.  
2. If the parent[id] == id, we know that id is the root node.  
3. The data structure using two methods Union() - union to nodes/components, and Find() - find the root node.  
4. We can do path compression, so after some number of Find() calls it will be O(1) to call Find() again.

### Minimum Spanning Tree (Union Find):  
A minimum spanning tree (MST) is a subset of the edges of a connected, edge-weighted undirected graph that connects all the vertices together, without any cycles and with the minimum possible total edge weight.  
Solution for Connecting Cities With Minimum Cost:  [https://leetcode.com/problems/connecting-cities-with-minimum-cost/](https://leetcode.com/problems/connecting-cities-with-minimum-cost/).

```
class UnionFind {
public:
	UnionFind(int n) : parent(n) {
		  iota(parent.begin(), parent.end(), 0);
	}
	int Find(int x) {
		int temp = x;
		while (temp != parent[temp]) {
			temp = parent[temp];
		}
		while (x != temp) {
			int next = parent[x];
			parent[x] = temp;
			x = next;
		}
		return temp;
	}
	bool Union(int x, int y) {
		int xx = Find(x);
		int yy = Find(y);
		if (xx == yy) return false;
		parent[xx] = yy;
		return true;
	}

private:
	vector<int> parent;
};
int minimumCost(int n, vector<vector<int>>& connections) {
	sort(connections.begin(), connections.end(), [](const auto& lhs, const auto& rhs){
		return lhs[2] < rhs[2];
	});
	UnionFind uf(n + 1);
	int sum = 0, count = 0;
	for (auto& c : connections) {
		if (uf.Union(c[0], c[1])) {
			count++;
			sum += c[2];
		}
		if (count == n - 1) return sum; // Return earlier once graph is connected.
	}
	return -1;
}

```

![image](https://assets.leetcode.com/users/images/8daae278-0e2f-4a1e-a9bd-4e1ffd586b63_1648921439.7056665.png)  
Visualization of Kruskal's algorithm: we will try to union nodes if they are not connected.  
**Notes**:  
1. One of the implementation of MST algorithm use Union Find algorithm (Kruskal's Algorithm).  
2. We need to sort elements by the weight before appying the algorithm, or we can use min priority_queue.

### Topological sort:
Is a linear ordering of its vertices such that for every directed edge uv from vertex u to vertex v, u comes before v in the ordering.

```
    // Kahn's Algorithm
    vector<vector<int>> adj(numCourses);
    vector<int> indegree(numCourses, 0);
    for (auto& p : prerequisites) {
        indegree[p[1]]++;
        adj[p[0]].push_back(p[1]);
    }
    queue<int> q;
    for (int i = 0; i < numCourses; i++) {
        if (indegree[i] == 0) q.push(i);
    }
    int prereq = 0;
    while (!q.empty()) {
        int el = q.front();
        q.pop();
        prereq++;
        for (auto& next : adj[el]) {
            if (--indegree[next] == 0) {
                q.push(next);
            }
        }
    }
    return prereq == numCourses;

```

![image](https://assets.leetcode.com/users/images/86fb9718-3b96-46b8-8b1f-7697449441ef_1648781045.0548813.png)  
The above picture demonstrates linear order of the given graph. The vertices can be tasks, and edges can represent some contraints, such as U should be finished before V in (U -> V).  
**Notes**:  
1. We will have the indegree array to count, which nods should be visited first.  
2. We will have a queue to push the nodes that don't have any dependencies.

### Bellman Ford:

Is an algorithm that computes shortest paths from a single source vertex to all of the other vertices in a weighted digraph.

```
class Solution {
public:
    int networkDelayTime(vector<vector<int>>& times, int n, int k) {
        vector<int> dist(n + 1, INT_MAX);
        dist[k] = 0;
        for (int i = 1; i <= n; i++) {
            for (auto& t : times) {
                if (dist[t[0]] != INT_MAX && dist[t[1]] > dist[t[0]] + t[2]) {
                    dist[t[1]] = dist[t[0]] + t[2];
                }
            }
        }
        int res = 0;
        for (int i = 1; i <= n; i++) {
            res = max(res, dist[i]);
        }
        return res == INT_MAX ? -1 : res;
    }
};

```

![image](https://assets.leetcode.com/users/images/615a0afc-e71f-4eed-80e8-b4bd7fba62aa_1649125105.5058165.png)  
The above picture demonstrates how the dist array incrementally updated with better values. If not a single value is updated during iteration - we can stop earlier.  
**Notes**:  
1. We will use the array to hold the distance between particular start node and all others.  
2. We will try to improve distance n times between all nodes in the graph.

### Floyd Warshall:

Is an algorithm for finding shortest paths in a directed weighted graph with positive or negative edge weights.

```
class Solution {
public:
    int networkDelayTime(vector<vector<int>>& times, int n, int k) {
        vector<vector<long>> dist(n, vector<long>(n, INT_MAX));
        for (auto& t : times)
            dist[t[0] - 1][t[1] - 1] = t[2];
        for (int i = 0; i < n; i++)
            dist[i][i] = 0;
        for (int k = 0; k < n; k++) {
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < n; j++) {
                    dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j]);
                }
            }
        }
        long res = INT_MIN;
        for (int i = 0; i < n; i++) {
            if (dist[k - 1][i] == INT_MAX) return -1;
            res = max(res, dist[k - 1][i]);
        }
        return (int)res;
    }
};

```

Vizualization for Floyd Warshall is slightly different from Bellman Ford, but the idea stays the same.  
**Notes**:  
1. We will use vector<vector> to keep track of distance between nodes i and j.  
2. We will have a 3 loops, checks if we can improve the distance between i and j by using k node.

### Eulearian Path:

Is an algorithm that finds a path that uses every  _**edge**_  in a graph only once.  
The algorithm below is a solution for the "**Reconstruct Itinerary**":  [https://leetcode.com/problems/reconstruct-itinerary/](https://leetcode.com/problems/reconstruct-itinerary/)

```
class Solution {
public:
    void dfs(unordered_map<string, multiset<string>>& graph,
             vector<string>& res, string start) {
        while (graph[start].size() > 0) {
            auto next = *graph[start].begin();
            graph[start].erase(graph[start].begin());
            dfs(graph, res, next);
        }
        res.push_back(start);
    }
    vector<string> findItinerary(vector<vector<string>>& tickets) {
        unordered_map<string, multiset<string>> graph;
        for (const auto& t : tickets) graph[t[0]].insert(t[1]);
        vector<string> res;
        dfs(graph, res, "JFK");
        reverse(res.begin(), res.end());
        return res;
    }
};

```

![image](https://assets.leetcode.com/users/images/9ca4dffd-5db0-4c68-b0ce-13edcc291b92_1647721389.4328434.png)  
The above picture is the visualization of eulerian path algorithm. You can observe how the result is constructed on the backtracking.  
**Notes**:  
1. The algorithm almost identical to the dfs traversal with one main instrumentation: we are building the path on the backtrack of the dfs algorithm:  `res.push_back(start);`  
2. That is why we should reverse the list at the end of the traversal:  `reverse(res.begin(), res.end());`  
3. In the above implementation we are using multiset (because of the problem), but the general implementation may use vector<> and additional vector<> to track the outgoing degrees, and use it for two main purposes: as index in the adj list, and to track how many node we not visited yet.