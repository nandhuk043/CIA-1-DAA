#include <stdio.h>
#include <stdlib.h>
#include <limits.h>

#define MAX_NODES 1000

int x;
int y;
int graph[MAX_NODES][MAX_NODES];
int dist[MAX_NODES];
int parent[MAX_NODES];
int visited[MAX_NODES];

int min_distance() {
    int min_dist = INT_MAX;
    int min_index = -1;

    for (int i = 0; i < x; i++) {
        if (!visited[i] && dist[i] < min_dist) {
            min_dist = dist[i];
            min_index = i;
        }
    }

    return min_index;
}

void prim(int start) {
    for (int i = 0; i < x; i++) {
        dist[i] = INT_MAX;
        visited[i] = 0;
    }
    dist[start] = 0;
    parent[start] = -1;

    for (int i = 0; i < x - 1; i++) {
        int u = min_distance();
        visited[u] = 1;

        for (int v = 0; v < x; v++) {
            if (graph[u][v] && !visited[v] && graph[u][v] < dist[v]) {
                parent[v] = u;
                dist[v] = graph[u][v];
            }
        }
    }
}

int main() {
    printf("Enter the number of nodes and edges: ");
    scanf("%d %d", &x, &y);

    printf("Enter the edges and their weights: ");
    for (int i = 0; i < y; i++) {
        int u, v, w;
        scanf("%d %d %d", &u, &v, &w);
        graph[u][v] = w;
    }

    printf("Enter the starting node: ");
    int start;
    scanf("%d", &start);

    prim(start);

    printf("Edge \tWeight\n");
    for (int i = 1; i < x; i++)
        printf("%d - %d \t%d\n", parent[i], i, dist[i]);

    return 0;
}
