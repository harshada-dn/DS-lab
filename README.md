# DS-lab
Exp-7
#include <stdio.h>
#include <conio.h>

#define MAX_VERTICES 10

struct Graph {
    int vertices;
    int adjMatrix[MAX_VERTICES][MAX_VERTICES];
};

void initializeGraph(struct Graph *g, int v) {
    int i, j;
    g->vertices = v;
    for (i = 0; i < v; i++) {
        for (j = 0; j < v; j++) {
            g->adjMatrix[i][j] = 0;
        }
    }
}

void addEdge(struct Graph *g, int src, int dest) {
    if (src >= 0 && src < g->vertices && dest >= 0 && dest < g->vertices) {
        g->adjMatrix[src][dest] = 1;
        g->adjMatrix[dest][src] = 1; // For undirected graph
    }
}

void displayMatrix(struct Graph *g) {
    int i, j;
    printf("\nAdjacency Matrix:\n");
    for (i = 0; i < g->vertices; i++) {
        for (j = 0; j < g->vertices; j++) {
            printf("%d ", g->adjMatrix[i][j]);
        }
        printf("\n");
    }
}

void main() {
    struct Graph g;
    int v, e, i;
    int src, dest;

    clrscr();

    printf("Enter number of vertices (max %d): ", MAX_VERTICES);
    scanf("%d", &v);

    initializeGraph(&g, v);

    printf("Enter number of edges: ");
    scanf("%d", &e);

    for (i = 0; i < e; i++) {
        printf("Enter edge %d (source and destination): ", i + 1);
        scanf("%d %d", &src, &dest);
        addEdge(&g, src, dest);
    }

    displayMatrix(&g);

    getch();
}
