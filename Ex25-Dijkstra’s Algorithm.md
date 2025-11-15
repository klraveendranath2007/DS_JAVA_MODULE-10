# Ex25 Finding the Fastest Route to a Charging Station using Dijkstra’s Algorithm
## DATE:
## AIM:
To design and implement a Python program that helps an electric vehicle (EV) find the shortest travel time from its current block to the nearest charging station using Dijkstra’s shortest path algorithm.
## Algorithm
1. Read number of blocks (nodes) and roads (edges) with travel times (weights).  
2. Build a weighted adjacency list for the graph.  
3. Read the list of charging station nodes.  
4. Run Dijkstra’s algorithm from the EV’s current location to compute shortest distances to all nodes.  
5. Find the minimum distance among all charging stations.  
6. Output the fastest route travel time and the corresponding charging station.     

## Program:
```
/*
Program to find the Fastest Route to a Charging Station using Dijkstra’s Algorithm
Developed by: K L RAVEENDRANATH
RegisterNumber:  212224060212
*/

import java.util.*;

class Edge {
    int to, weight;
    Edge(int to, int weight) { this.to = to; this.weight = weight; }
}

public class FastestChargingRoute {

    static int[] dijkstra(List<List<Edge>> graph, int src) {
        int n = graph.size();
        int[] dist = new int[n];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[src] = 0;
        PriorityQueue<int[]> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a[1]));
        pq.add(new int[]{src, 0});
        
        while (!pq.isEmpty()) {
            int[] curr = pq.poll();
            int u = curr[0], d = curr[1];
            if (d > dist[u]) continue;
            for (Edge e : graph.get(u)) {
                if (dist[u] + e.weight < dist[e.to]) {
                    dist[e.to] = dist[u] + e.weight;
                    pq.add(new int[]{e.to, dist[e.to]});
                }
            }
        }
        return dist;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of blocks (nodes): ");
        int n = sc.nextInt();
        System.out.print("Enter number of roads (edges): ");
        int m = sc.nextInt();
        
        List<List<Edge>> graph = new ArrayList<>();
        for (int i = 0; i < n; i++) graph.add(new ArrayList<>());
        
        System.out.println("Enter roads as (u v travelTime) with 0-based indices:");
        for (int i = 0; i < m; i++) {
            int u = sc.nextInt();
            int v = sc.nextInt();
            int w = sc.nextInt();
            graph.get(u).add(new Edge(v, w));
            graph.get(v).add(new Edge(u, w));
        }

        System.out.print("Enter number of charging stations: ");
        int k = sc.nextInt();
        int[] stations = new int[k];
        System.out.println("Enter charging station nodes (0-based):");
        for (int i = 0; i < k; i++) stations[i] = sc.nextInt();

        System.out.print("Enter current block of EV (0-based): ");
        int start = sc.nextInt();

        int[] dist = dijkstra(graph, start);
        int minDist = Integer.MAX_VALUE;
        int nearestStation = -1;
        for (int station : stations) {
            if (dist[station] < minDist) {
                minDist = dist[station];
                nearestStation = station;
            }
        }

        if (nearestStation == -1 || minDist == Integer.MAX_VALUE)
            System.out.println("No reachable charging station.");
        else
            System.out.println("Nearest charging station: " + nearestStation + " with travel time: " + minDist);

        sc.close();
    }
}
```

## Output:
<img width="705" height="479" alt="image" src="https://github.com/user-attachments/assets/18706bd8-51cd-404d-83e1-1a913fc950c6" />



## Result:
The program has been successfully implemented and executed.
It uses Dijkstra’s algorithm to determine the shortest travel time from the EV’s current location to the nearest charging station and correctly handles cases where no station is reachable.
