# Algorithms

- [Sorting algorithms](#sorting-algorithms)
  - [Quicksort](#quicksort)
  - [Selection Sort](#selection-sort)
- [Search algorithms](#search-algorithms)
  - [Binary Search](#binary-search)
  - [Breadth-first search](#breadth-first-search)
  - [Dijkstra](#dijkstra)

--- 
 
## Sorting algorithms

### Quicksort

```python

import random

def qsort(array):
  if len(array) < 2:
    return array
  axis = random.choice(array)
  lower = [x for x in array if x < axis]
  greater = [x for x in array if x > axis]

  return qsort(lower)+[axis]+qsort(greater)
```

### Selection Sort

```python

def find_minimum(array):
    minimum = array[0]
    idx_min = 0
    for i in range(1, len(array)):
        if minimum > array[i]:
            minimum = array[i]
            idx_min = i

    return idx_min

def selection_sort(array):
    new_array = []
    for i in range(0, len(array)):
        idx = find_minimum(array)
        new_array.append(array.pop(idx))

    return new_array
```

## Search algorithms

### Binary search

```python
def binary_search(array, value):
    min_ = 0
    max_ = len(array)-1
    while min_ <= max_:
        med = int((min_+ max_)/2)
        pred_val = array[med]
        if pred_val == value:
            return med
        elif pred_val < value:
            min_ = med + 1
        else:
            max_ = med -1

    return None
```

### Breadth-first search

```python

from collections import deque

def is_seller(value):
    return value[-1] == 'm'

def bfs(graph, node):
    queue = deque()
    queue += graph[node]
    visited = []

    while queue:
        value = queue.popleft()
        if value not in visited:
            if is_seller(value):
                print("The seller is " + value)
                return True
            else:
                queue += graph[value]
                visited.append(value)

    return False

```

### Dijkstra

```python

def find_node_minor_cost(costs, processed):
    minor_cost = float("inf")
    minor_cost_node = None
    for node in costs:
        cost = costs[node]
        if cost < minor_cost and node not in processed:
            minor_cost = cost
            minor_cost_node = node

    return minor_cost_node

def dijkstra(graph, costs, fathers):
    processed = []
    node = find_node_minor_cost(costs, processed)
    while node is not None:
        cost = costs[node]
        if cost < 0:
            raise Exception("The cost of the node is negative. Dijkstra cannot handle this")

        neighbors = graph[node]
        for n in neighbors.keys():
            new_cost = cost + neighbors[n]
            if costs[n] > new_cost:
                costs[n] = new_cost
                fathers[n] = node

        processed.append(node)
        node = find_node_minor_cost(costs, processed)

    return list(costs.items())[-1][-1]

```
