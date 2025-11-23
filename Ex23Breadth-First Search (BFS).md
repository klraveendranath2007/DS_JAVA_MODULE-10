# Ex23 Breadth-First Search (BFS) Traversal of a City Junction Map
## DATE:30-10-2025
## AIM:
To design and implement a Python program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph, and find all reachable locations from a given source junction.
## Algorithm
1. Start the program.  
2. Read the number of junctions (vertices) and roads (edges).  
3. Build an adjacency list to represent the graph.  
4. Read the source junction.  
5. Use a queue and a visited array to perform BFS.  
6. Print the order of traversal showing all reachable junctions.  
7. Stop the program.   

## Program:
```java
/*
Program to perform Breadth-First Search (BFS) traversal on a city’s junction map represented as a graph
Developed by: K L RAVEENDRANATH
RegisterNumber:  212224060212
*/
import java.util.*;

public class EmergencyRouteBFS {
    public static void addEdge(List<List<Integer>> g, int u, int v) {
        g.get(u).add(v);
        g.get(v).add(u);
    }

    public static void bfs(List<List<Integer>> g, int src, boolean[] visited) {
        Queue<Integer> q = new LinkedList<>();
        q.offer(src);
        visited[src] = true;
        while (!q.isEmpty()) {
            int curr = q.poll();
            System.out.print(curr + " ");
            for (int neighbor : g.get(curr)) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    q.offer(neighbor);
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(), e = sc.nextInt();
        List<List<Integer>> g = new ArrayList<>();
        for (int i = 0; i < n; i++) g.add(new ArrayList<>());
        for (int i = 0; i < e; i++) addEdge(g, sc.nextInt(), sc.nextInt());
        int src = sc.nextInt();
        bfs(g, src, new boolean[n]);
    }
}
```

## Output:
<img width="386" height="250" alt="image" src="https://github.com/user-attachments/assets/8107fb0c-a9c1-4b34-8981-fb57600a865a" />




## Result:
The program has been successfully implemented and executed.
It performs Breadth-First Search (BFS) traversal on a city junction map and correctly lists all reachable locations from the given source node.
