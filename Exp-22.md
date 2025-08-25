#include <stdio.h>

int main() {
    int vertices, i, j;
    
    printf("Enter number of vertices: ");
    scanf("%d", &vertices);

    int graph[vertices][vertices];

    printf("Enter adjacency matrix (0 or 1):\n");
    for(i = 0; i < vertices; i++) {
        for(j = 0; j < vertices; j++) {
            scanf("%d", &graph[i][j]);
        }
    }

    // Display adjacency matrix
    printf("Adjacency Matrix:\n");
    for(i = 0; i < vertices; i++) {
        for(j = 0; j < vertices; j++) {
            printf("%d ", graph[i][j]);
        }
        printf("\n");
    }

    return 0;
}
