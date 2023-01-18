#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_VERTICES 100
#define MAX_EDGES 1000

int parent[MAX_VERTICES];

struct Edge {
    int u, v, weight;
} edges[MAX_EDGES];

int cmp(const void* a, const void* b) {
    return ((struct Edge*) a)->weight - ((struct Edge*) b)->weight;
}

int find(int x) {
    if (parent[x] == x) {
        return x;
    }
    return parent[x] = find(parent[x]);
}

void kruskal(int n, int m) {
    qsort(edges, m, sizeof(struct Edge), cmp);

    for (int i = 0; i < n; i++) {
        parent[i] = i;
    }

    int count = 0, totalWeight = 0;
    for (int i = 0; i < m; i++) {
        int u = find(edges[i].u), v = find(edges[i].v);
        if (u != v) {
            parent[u] = v;
            printf("%d %d %d\n", edges[i].u, edges[i].v, edges[i].weight);
            totalWeight += edges[i].weight;
            count++;
        }
        if (count == n - 1) {
            break;
        }
    }
    printf("Total weight: %d\n", totalWeight);
}

int main() {
    int n, m;
    scanf("%d %d", &n, &m);
    for (int i = 0; i < m; i++) {
        int u, v, w;
        scanf("%d %d %d", &u, &v, &w);
        edges[i] = (struct Edge) {u, v, w};
    }
    kruskal(n, m);
    return 0;
}
