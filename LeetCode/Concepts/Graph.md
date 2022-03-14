# Graph Concepts:

## DFS:

### Python:

```
from collections import deque

class Solution(object):
    
    def cloneGraph(self, node):
        """
        :type node: Node
        :rtype: Node
        """
        if not node:
            return node
        
        visited = {}
        
        queue = deque([node])
        
        visited[node] = Node(node.val, [])
        
        while queue:
            n = queue.popleft()
            
            for neighbor in n.neighbors:
                if neighbor not in visited:
                    
                    visited[neighbor] = Node(neighbor.val, [])

                    queue.append(neighbor)

                visited[n].neighbors.append(visited[neighbor])
                
        return visited[node]
```

## BFS:

### Python

```
class Solution(object):
    def __init__(self):
        self.visited = {}
    
    def cloneGraph(self, node):
        """
        :type node: Node
        :rtype: Node
        """
        if not node:
            return node
        
        if node in self.visited:
            return self.visited[node]
        
        new_node = Node(node.val, [])
        
        self.visited[node] = new_node
        
        if node.neighbors:
            new_node.neighbors = [self.cloneGraph(n) for n in node.neighbors]
            
        return new_node
```

