# 📊 Graph Algorithms for Real-World Applications

* **Student:** Aditya Singh
* **Course:** Design and Analysis of Algorithms Lab (ENCA351)
* **Program:** BCA (AI & Data Science)
* **Session:** 2025-26
* **Faculty:** Dr. Aarti Sangwan

---

## 🎯 Assignment 3: Solving Real-World Problems Using Graph Algorithms

This project implements and analyzes four fundamental graph algorithms to solve practical, real-world problems. The applications range from social networking and navigation systems to emergency response and infrastructure planning.

The core learning objective is to map these real-world scenarios to graph data structures and then apply the most appropriate algorithm (like BFS, Bellman-Ford, Dijkstra, and MST) to find an optimal solution.

---

## 🚀 Instructions to Run Code

### 1. Setup Environment

Before running the notebook, please install the required Python libraries.

1.  **Clone the repository:**
    ```bash
    git clone [Your GitHub Repo URL]
    cd [Your Repo Name]
    ```

2.  **Create and activate a virtual environment (recommended):**
    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Create a `requirements.txt` file:**
    Create a file named `requirements.txt` with the following content:
    ```
    pandas
    networkx
    matplotlib
    memory_profiler
    ```

4.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

### 2. Execute the Notebook

1.  Open the `Graph_Algorithms_for_Real_World_Applications.ipynb` file in a Jupyter environment like Google Colab, VS Code, or Jupyter Lab.
2.  Run all cells sequentially from top to bottom.
3.  The output plots will be saved to the `images/` directory, and the CSV data tables will be saved to the `tables/` directory.

---

## 📊 Analysis and Algorithm Justification

This section details the algorithm chosen for each problem and the justification for its use based on time complexity and problem constraints.

### 1. Problem 1: Social Network Friend Suggestion

* **Algorithm:** Breadth-First Search (BFS)
* **Justification:** The goal is to find "friends of friends," which are nodes at exactly distance 2 from the source user. BFS is the optimal algorithm for finding the shortest path in an unweighted graph, as it explores the graph in "layers." This makes it trivial to identify all nodes at level 1 (direct friends) and level 2 (friends of friends).
* **Time Complexity:** $O(V+E)$, where V is the number of users and E is the number of friendships. This is because every user (vertex) and friendship (edge) is visited exactly once.

### 2. Problem 2: Route Finding with Negative Weights

* **Algorithm:** Bellman-Ford
* **Justification:** This problem specifies finding the shortest path in a graph that *may include negative edge weights* (e.g., a route that has a subsidy or rebate). Dijkstra's algorithm fails in the presence of negative weights because its greedy approach (always picking the "lightest" edge) is no longer guaranteed to be optimal. Bellman-Ford is specifically designed to handle negative weights. It also has the added benefit of being able to detect negative weight cycles, which would represent an impossible scenario (like a route that *earns* you time).
* **Time Complexity:** $O(V \cdot E)$, as the algorithm must relax *all* E edges V-1 times in the worst case.

### 3. Problem 3: Emergency Response (Shortest Path)

* **Algorithm:** Dijkstra's Algorithm
* **Justification:** This objective is to find the *fastest* (i.e., shortest path) route in a city map where all travel times (weights) are positive. This is the classic use case for Dijkstra's. By using a min-heap (priority queue), it efficiently explores the graph, always expanding the node with the current shortest path, guaranteeing an optimal solution much faster than Bellman-Ford.
* **Time Complexity:** $O(E \log V)$ with a min-heap implementation, which is significantly faster than Bellman-Ford's $O(VE)$.

### 4. Problem 4: Network Cable Installation (MST)

* **Algorithm:** Minimum Spanning Tree (Kruskal's and Prim's)
* **Justification:** The goal is not to find a path between two points, but to *connect all nodes* (offices) with the *minimum total cost* (cable length). This is the textbook definition of a Minimum Spanning Tree (MST). Both Kruskal's (using Union-Find to avoid cycles) and Prim's (using a priority queue to grow the tree) are greedy algorithms that provably find the minimum total cost for a connected, undirected graph.
* **Time Complexity:** $O(E \log V)$ for both algorithms when implemented efficiently (Kruskal's with path compression or Prim's with a binary heap).

---

## 📈 Final Summary

### Algorithm Summary Table

| Problem | Graph Algorithm | Time Complexity | Application Domain | Notes |
| :--- | :--- | :--- | :--- | :--- |
| Social Network Suggestion | BFS/DFS | $O(V+E)$ | Social Media | Suggest mutual friends |
| Google Maps Routing | Bellman-Ford | $O(VE)$ | Navigation | Works with negative weights |
| Emergency Path Planning | Dijkstra's | $O(E \log V)$ | Disaster Response | Fastest path in a positive-weighted map |
| Cable Installation | MST (Prim/Kruskal) | $O(E \log V)$ | Infrastructure | Minimum cable cost |

### Reflections on Context

This assignment clearly demonstrated how the **real-world context directly dictates the algorithm choice**.

* For finding "friends of friends," the problem is about *levels*, not *cost*. An unweighted algorithm like **BFS** is therefore the most direct and efficient tool.
* For pathfinding, the choice between **Dijkstra's** and **Bellman-Ford** is entirely dependent on the *constraints* of the edge weights. If all weights are positive (like travel time), Dijkstra's is vastly superior. But the moment negative weights are possible (like subsidized routes), Dijkstra's fails, and **Bellman-Ford** becomes the necessary, albeit slower, solution.
* Finally, for connecting a network, the problem wasn't about a *path* from A to B, but about *total connectivity* for the lowest cost. This fundamentally changes the problem from "shortest path" to "minimum spanning tree," requiring **Kruskal's** or **Prim's**.

---

## 📚 References and Acknowledgments

* **Core Concepts:** *Introduction to Algorithms* (CLRS) by Cormen, Leiserson, Rivest, and Stein.
* **Libraries:** `networkx` and `matplotlib` were used for graph visualization. `memory_profiler` was used for performance analysis.
* **Faculty:** Dr. Aarti Sangwan for the assignment and guidance.
