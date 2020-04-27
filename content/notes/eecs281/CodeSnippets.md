---
title: Code Snippets
linktitle: Code Snippets
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  example:
    parent: Final Topics
    weight: 1

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1




---

## Minimum Required Nodes in AVL Tree for tree of height h

```c++
// One half of the tree must be minimum height h-1 (excluding root), the other
// must be minimum height h-2 (excluding root) then add one for the root
//
//                   one half of tree       other half     root
min_nodes_AVL(h) = min_nodes_AVL(h-1) + min_nodes_AVL(h-2) + 1
```

## Breadth-First Search

```c++
void Graph::BFS(int s) 
{ 
    // Mark all the vertices as not visited 
    bool *visited = new bool[V]; 
    for(int i = 0; i < V; i++) 
        visited[i] = false; 
  
    // Create a queue for BFS 
    list<int> queue; 
  
    // Mark the current node as visited and enqueue it 
    visited[s] = true; 
    queue.push_back(s); 
  
    // 'i' will be used to get all adjacent 
    // vertices of a vertex 
    list<int>::iterator i; 
  
    while(!queue.empty()) 
    { 
        // Dequeue a vertex from queue and print it 
        s = queue.front(); 
        cout << s << " "; 
        queue.pop_front(); 
  
        // Get all adjacent vertices of the dequeued 
        // vertex s. If a adjacent has not been visited,  
        // then mark it visited and enqueue it 
        for (i = adj[s].begin(); i != adj[s].end(); ++i) 
        { 
            if (!visited[*i]) 
            { 
                visited[*i] = true; 
                queue.push_back(*i); 
            } 
        } 
    } 
} 
```

## Depth-First Search

```c++
void Graph::DFS(int s) 
{ 
    // Initially mark all verices as not visited 
    vector<bool> visited(V, false); 
  
    // Create a stack for DFS 
    stack<int> stack; 
  
    // Push the current source node. 
    stack.push(s); 
  
    while (!stack.empty()) 
    { 
        // Pop a vertex from stack and print it 
        s = stack.top(); 
        stack.pop(); 
  
        // Stack may contain same vertex twice. So 
        // we need to print the popped item only 
        // if it is not visited. 
        if (!visited[s]) 
        { 
            cout << s << " "; 
            visited[s] = true; 
        } 
  
        // Get all adjacent vertices of the popped vertex s 
        // If a adjacent has not been visited, then push it 
        // to the stack. 
        for (auto i = adj[s].begin(); i != adj[s].end(); ++i) 
            if (!visited[*i]) 
                stack.push(*i); 
    } 
} 
```

## Finding if node exists 

### Recursive Solution

```c++
bool exists(Node* node, int val) {
    if (node == nullptr) return false;
    if (node->val == val) return true;
    if (val < node->val) {
        return exists(node->left, val);
    }
    else {
        return exists(node->right, val);
    }
    return false
}
```

### Iterative Solution

```c++
bool exists(Node* node, int val) {
    Node* current_node = node;
    while (current_node != nullptr) {
        if (val == current_node->val) return true;
        if (val < current_node->val) current_node = current_node->left;
        else current_node = current_node->right;
    }
    return false;
}
```



