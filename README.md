# Silver-Hat

tfgjfghjtfg
gdfgd
htfghftgtj
India
Djiktra's theoram-shortest path


Djiktra's algorithm


Dijkstra doesn’t work for Graphs with negative weight edges, Bellman-Ford works for such graphs.


import java.util.*; 
import java.lang.*; 
import java.io.*; 
  

class ShortestPath { 
    
    static final int V = 9; 
    int minDistance(int dist[], Boolean sptSet[]) 
    { 
      
        int min = Integer.MAX_VALUE, min_index = -1; 
  
        for (int v = 0; v < V; v++) 
            if (sptSet[v] == false && dist[v] <= min) { 
                min = dist[v]; 
                min_index = v; 
            } 
  
        return min_index; 
    } 

    void printSolution(int dist[]) 
    { 
        System.out.println("Vertex \t\t Distance from Source"); 
        for (int i = 0; i < V; i++) 
            System.out.println(i + " \t\t " + dist[i]); 
    } 
 
    void dijkstra(int graph[][], int src) 
    { 
        int dist[] = new int[V]; // The output array. dist[i] will hold 
   
        Boolean sptSet[] = new Boolean[V]; 
  
        for (int i = 0; i < V; i++) { 
            dist[i] = Integer.MAX_VALUE; 
            sptSet[i] = false; 
        } 
  
        dist[src] = 0; 
  
        for (int count = 0; count < V - 1; count++) { 
         
            int u = minDistance(dist, sptSet); 
  
            
            sptSet[u] = true; 
  
          
            for (int v = 0; v < V; v++) 
  
            
                if (!sptSet[v] && graph[u][v] != 0 && dist[u] != Integer.MAX_VALUE && dist[u] + graph[u][v] < dist[v]) 
                    dist[v] = dist[u] + graph[u][v]; 
        } 
  
        printSolution(dist); 
    }

class Graph { 
   
    class Edge { 
        int src, dest, weight; 
        Edge() 
        { 
            src = dest = weight = 0; 
        } 
    }; 
  
    int V, E; 
    Edge edge[]; 
  
    Graph(int v, int e) 
    { 
        V = v; 
        E = e; 
        edge = new Edge[e]; 
        for (int i = 0; i < e; ++i) 
            edge[i] = new Edge(); 
    } 
  
   
    void BellmanFord(Graph graph, int src) 
    { 
        int V = graph.V, E = graph.E; 
        int dist[] = new int[V]; 
  
    
        for (int i = 0; i < V; ++i) 
            dist[i] = Integer.MAX_VALUE; 
        dist[src] = 0; 
  
  
        for (int i = 1; i < V; ++i) { 
            for (int j = 0; j < E; ++j) { 
                int u = graph.edge[j].src; 
                int v = graph.edge[j].dest; 
                int weight = graph.edge[j].weight; 
                if (dist[u] != Integer.MAX_VALUE && dist[u] + weight < dist[v]) 
                    dist[v] = dist[u] + weight; 
            } 
        } 
  
       
        for (int j = 0; j < E; ++j) { 
            int u = graph.edge[j].src; 
            int v = graph.edge[j].dest; 
            int weight = graph.edge[j].weight; 
            if (dist[u] != Integer.MAX_VALUE && dist[u] + weight < dist[v]) { 
                System.out.println("Graph contains negative weight cycle"); 
                return; 
            } 
        } 
        printArr(dist, V); 
    } 
    void printArr(int dist[], int V) 
    { 
        System.out.println("Vertex Distance from Source"); 
        for (int i = 0; i < V; ++i) 
            System.out.println(i + "\t\t" + dist[i]); 
    } 
  
  

Dijkstra doesn’t work for Graphs with negative weight edges, Bellman-Ford works for such graphs.


