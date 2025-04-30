# CMPS 2200 Assignment 5
## Answers

**Name:** Lulu Sawaf






- **1a.**
max depth: log_base d(n)

- **1b.**
delete-min= O(dlog_base d(n))
insert = O(log_base d(n))

- **1c.**
O(|V} * dlog_base d|V| + |E| * dlo_base d |V|)
- **1d.**
d = |E| / |V|

- **2a.**

| i → j | APSP(i,j,-1) |
|------|---------------|
| 0→0  | 0             |
| 0→1  | -2            |
| 0→2  | 2             |
| 1→0  | ∞             |
| 1→1  | 0             |
| 1→2  | 1             |
| 2→0  | ∞             |
| 2→1  | 1             |
| 2→2  | 0             |

k=0
0→1: min(-2, 0 + (-2)) = -2

0→2: min(2, 0 + 2) = 2

1→2: min(1, ∞ + 2) = 1

1→1: min(0, ∞ + (-2)) = 0

1→0: min(∞, ∞ + 0) = ∞

2→1: min(1, ∞ + (-2)) = 1

2→2: min(0, ∞ + 2) = 0

k=1
| i→j  | APSP(i,j,1) |
|------|-------------|
| 0→1  | -2          |
| 0→2  | -1          |
| 1→2  | 1           |
| 2→1  | 1           |
| ...  | others unchanged |

k=2
| i → j | APSP(i,j,2) |
|-------|-------------|
| 0→0   | 0           |
| 0→1   | -2          |
| 0→2   | -1          |
| 1→0   | ∞           |
| 1→1   | 0           |
| 1→2   | 1           |
| 2→0   | ∞           |
| 2→1   | 1           |
| 2→2   | 0           |

- **2b.**
APSP(i,j,2) = min(APSP(i,j,1), APSP(i,2,1) + APSP(2,j,1))

- **2c.**
APSP(i,j,k)=min(APSP(i,j,k−1), APSP(i,k,k−1)+APSP(k,j,k−1))
The shortest path from i to j using nodes {0,...,k} is either:
The path that doesn't go through k, or
A shorter path that does go through k.

- **2d.**
So total subproblems = n^3, work = O(n^3)

- **2e.**
This algorithm is better when the graph is dense (E = O(V²)) or negative edge weights are present.
Johnson’s algorithm is better for sparse graphs (E ≪ V²), especially if no negative weights are present.

- **3a.**
MST is not always the solution to MMET. MST looks to minimize total weight. MMET looks to minimize median weight.

- **3b.**
Compute MST T (kruskal)
For each edge e not in MST:
Add e to T (creates cycle)
Remove the largest weight edge e in the cycle
Form a new spanning tree T'= T + e - e'
Record the weight of T'
Among all such T', pick the one with minimal total weight > weight of MST

- **3c.**
O(ElogE = nE)
