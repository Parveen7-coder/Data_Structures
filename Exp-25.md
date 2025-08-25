#include <stdio.h>
#define INF 9999
#define MAX 10

int minDistance(int dist[], int visited[], int n) {
    int min = INF, min_index;
    for(int i = 0; i < n; i++) {
        if(!visited[i] && dist[i] <= min) {
            min = dist[i];
            min_index = i;
        }
    }
    return min_index;
}

void dijkstra(int graph[MAX][MAX], int n, int source) {
    int dist[MAX], visited[MAX] = {0};

    for(int i = 0; i < n; i++)
        dist[i] = INF;
    dist[source] = 0;

    for(int count = 0; count < n-1; count++) {
        int u = minDistance(dist, visited, n);
        visited[u] = 1;

        for(int v = 0; v < n; v++) {
            if(!visited[v] && graph[u][v] && dist[u] + graph[u][v] < dist[v])
                dist[v] = dist[u] + graph[u][v];
        }
    }

    printf("Vertex\tDistan
