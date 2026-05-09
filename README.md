# design-analysis-and-algorithms-
learning codes of data structures 




def quicksort(arr):
    if len(arr) <= 1:
        return arr

    pivot = arr[0]

    left = []
    right = []

    for i in arr[1:]:
        if i < pivot:
            left.append(i)
        else:
            right.append(i)

    return quicksort(left) + [pivot] + quicksort(right)


# Example
numbers = [5, 3, 8, 4, 2, 7, 1}

print("Before sorting:", numbers)

sorted_numbers = quicksort(numbers)

print("After sorting:", sorted_numbers)

Before sorting: [5, 3, 8, 4, 2, 7, 1]
After sorting: [1, 2, 3, 4, 5, 7, 8]


# merge sort c code 

#include <stdio.h>

void merge(int a[], int l, int m, int r) {
    int i = l, j = m + 1, k = 0, temp[100];

    while (i <= m && j <= r)
        temp[k++] = (a[i] < a[j]) ? a[i++] : a[j++];

    while (i <= m)
        temp[k++] = a[i++];

    while (j <= r)
        temp[k++] = a[j++];

    for (i = l, k = 0; i <= r; i++, k++)
        a[i] = temp[k];
}

void mergeSort(int a[], int l, int r) {
    if (l < r) {
        int m = (l + r) / 2;
        mergeSort(a, l, m);
        mergeSort(a, m + 1, r);
        merge(a, l, m, r);
    }
}

int main() {
    int a[] = {38, 27, 43, 3, 9, 82, 10};
    int n = 7, i;

    mergeSort(a, 0, n - 1);

    printf("Sorted array: ");
    for (i = 0; i < n; i++)
        printf("%d ", a[i]);

    return 0;
}








#transitive closure using warshalls algorithm code in c


#include <stdio.h>

#define V 4 // Number of vertices

void printMatrix(int matrix[V][V]) {
    for (int i = 0; i < V; i++) {
        for (int j = 0; j < V; j++)
            printf("%d ", matrix[i][j]);
        printf("\n");
    }
}

void transitiveClosure(int graph[V][V]) {
    int reach[V][V], i, j, k;

    // Initialize reachability matrix with input graph
    for (i = 0; i < V; i++)
        for (j = 0; j < V; j++)
            reach[i][j] = graph[i][j];

    // Core Warshall's Logic
    for (k = 0; k < V; k++) {
        for (i = 0; i < V; i++) {
            for (j = 0; j < V; j++) {
                // If vertex k is an intermediate, update reachability
                reach[i][j] = reach[i][j] || (reach[i][k] && reach[k][j]);
            }
        }
    }

    printf("Transitive Closure Matrix:\n");
    printMatrix(reach);
}

int main() {
    int graph[V][V] = { {1, 1, 0, 1},
                        {0, 1, 1, 0},
                        {0, 0, 1, 1},
                        {0, 0, 0, 1} };

    transitiveClosure(graph);
    return 0;
}
