<h1>ExpNo 2 : Implement Depth First Search Traversal of a Graph</h1> 
<h3>Name: Sadhana S </h3>
<h3>Register Number: 212224230234   </h3>
<H3>Aim:</H3>
<p> To Implement Depth First Search Traversal of a Graph using Python 3.</p>
<h3>Theory:</h3>
<strong>Depth First Traversal </strong>(or DFS) for a graph is like Depth First Traversal of a tree. The only catch here is that, unlike trees, graphs may contain cycles (a node may be visited twice). Use a Boolean visited array to avoid processing a node more than once. A graph can have more than one DFS traversal. 
Depth-first search is an algorithm for traversing or searching trees or graph data structures. The algorithm starts at the root node (selecting some arbitrary node as the root node in the case of a graph) and explores as far as possible along each branch before backtracking.
Step 1: Initially, stack and visited arrays are empty.

 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/640b3c6f-3ac1-49a2-a955-68da9a71f446)


Queue and visited arrays are empty initially.
Stack and visited arrays are empty initially.
Step 2: Visit 0 and put its adjacent nodes which are not visited yet into the stack.
 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/86dcf7d9-1f9d-49b0-a821-5976a6e77606)

 Visit node 0 and put its adjacent nodes (1, 2, 3) into the stack
 Visit node 0 and put its adjacent nodes (1, 2, 3) into the stack

Step 3: Now, Node 1 at the top of the stack, so visit node 1 and pop it from the stack and put all of its adjacent nodes which are not visited in the stack.
 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/e6017942-08b1-4742-87ad-c97eb97bf985)

Visit node 1
 Visit node 1

Step 4: Now, Node 2 at the top of the stack, so visit node 2 and pop it from the stack and put all of its adjacent nodes which are not visited (i.e, 3, 4) in the stack.
 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/6e6d123c-60ae-4f9c-a27c-c4fc7e57d57c)

 Visit node 2 and put its unvisited adjacent nodes (3, 4) into the stack
 Visit node 2 and put its unvisited adjacent nodes (3, 4) into the stack

Step 5: Now, Node 4 at the top of the stack, so visit node 4 and pop it from the stack and put all of its adjacent nodes which are not visited in the stack.
 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/20b76a05-5668-4da5-8189-e10fb1bb7238)

 Visit node 4
 Visit node 4

Step 6: Now, Node 3 at the top of the stack, so visit node 3 and pop it from the stack and put all of its adjacent nodes which are not visited in the stack.
 ![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/3b88f04a-7846-4f75-89b4-22bbd5b48e52)

Visit node 3
Visit node 3

Now, the Stack becomes empty, which means we have visited all the nodes, and our DFS traversal ends.

<h3>Algorithm:</h3>
<B><ol>
 <li>Construct a Graph with Nodes and Edges</li>
 <li>Depth First Search Uses Stack and Recursion</li>
 <li>Insert a START node to the STACK</li>
 <li>Find its Successors Or neighbors and Check whether the node is visited or not</li>
 <li>If Not Visited, add it to the STACK. Else Call The Function Again Until No more nodes needs to be visited.</li>
</ol></B>

PROGRAM
```
from collections import defaultdict

def dfs(graph, start):
    visited = defaultdict(bool)
    path = []
    stack = [start]  

    while stack:
        node = stack.pop()  
        if not visited[node]:
            visited[node] = True
            path.append(node)

            for neighbour in reversed(graph[node]):
                if not visited[neighbour]:
                    stack.append(neighbour)
    return path

n, m = map(int, input().split())  
graph = defaultdict(list)
vertices = set()

count = 0
while count < m:
    line = input().strip()
    if not line:   
        continue
    u, v = line.split()
    graph[u].append(v)
    graph[v].append(u)
    vertices.add(u)
    vertices.add(v)
    count += 1

if "0" in vertices:
    start = "0"
elif "A" in vertices:
    start = "A"
else:
    start = sorted(vertices)[0]  

traversal = dfs(graph, start)
print(traversal)
```

<hr>
<h3>Sample Input</h3>
<hr>
8 9 <BR>
A B <BR>
A C <BR>
B E <BR>
C D <BR>
B D <BR>
C G <BR>
D F <BR>
G F <BR>
F H <BR>
<hr>
<h3>Sample Output</h3>
<hr>
['A', 'B', 'E', 'D', 'C', 'G', 'F', 'H']

<hr>
Input 

<img width="82" height="524" alt="Screenshot 2025-08-29 112621" src="https://github.com/user-attachments/assets/20640d1f-ed34-42c1-bd77-8a8ebbc6809e" />

Output

<img width="447" height="130" alt="Screenshot 2025-08-29 112652" src="https://github.com/user-attachments/assets/00dc25aa-2528-41ae-a3e3-019943943aea" />


<hr>
<h3>Sample Input</h3>
<hr>
5 5 <BR>
0 1 <BR>
0 2 <BR>
0 3 <BR>
2 3 <BR>
2 4 <BR>
<hr>
<h3>Sample Output</h3>
<hr>
['0', '1', '2', '3', '4']

Input

<img width="70" height="298" alt="Screenshot 2025-08-29 112741" src="https://github.com/user-attachments/assets/e2e1e910-7b92-4356-874f-3c8a85cf2e18" />

Output

<img width="383" height="104" alt="Screenshot 2025-08-29 112817" src="https://github.com/user-attachments/assets/b6b5e525-753f-4eee-ba87-139552fe6cae" />


<hr>
<h3>Result:</h3>
<hr>
<p>Thus,a Graph was constructed and implementation of Depth First Search for the same graph was done successfully.</p>

