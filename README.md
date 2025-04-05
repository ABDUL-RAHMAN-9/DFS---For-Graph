# DFS-For-Graph
<div>
  <p>
    <h3>
    -  In Depth First Search (or DFS) for a graph, we traverse all adjacent vertices one by one. When we traverse an adjacent vertex, we completely finish the traversal of all vertices reachable through that adjacent vertex. This is similar to a tree, where we first completely traverse the left subtree and then move to the right subtree. The key difference is that, unlike trees, graphs may contain cycles (a node may be visited more than once). To avoid processing a node multiple times, we use a boolean visited array.
      </h3>
  </p>
  <h2><b><i>Problem:</i></b></h2>
  <p>
  -  Given a connected undirected graph containing V vertices represented by a 2-d adjacency list adj[][], where each adj[i] represents the list of vertices connected to vertex i. Perform a Depth First Search (DFS) traversal starting from vertex 0, visiting vertices from left to right as per the given adjacency list, and return a list containing the DFS traversal of the graph.

* Note: Do traverse in the same order as they are in the given adjacency list.
  <h2>Example:</h2>
  <p>
```
    Input: adj[][] = [[2, 3, 1], [0], [0, 4], [0], [2]]
```

<div align="center">
  <img src="https://media.geeksforgeeks.org/img-practice/prod/addEditProblem/700203/Web/Other/blobid0_1728647807.jpg" alt="Centered Image" width="500" height="300">
</div>

```
Output: [0, 2, 4, 3, 1]
Explanation: Starting from 0, the DFS traversal proceeds as follows:
Visit 0 → Output: 0 
Visit 2 (the first neighbor of 0) → Output: 0, 2 
Visit 4 (the first neighbor of 2) → Output: 0, 2, 4 
Backtrack to 2, then backtrack to 0, and visit 3 → Output: 0, 2, 4, 3 
Finally, backtrack to 0 and visit 1 → Final Output: 0, 2, 4, 3, 1
```
<h2>Program:</h2>
  
```

#include <bits/stdc++.h>
using namespace std;

class Solution {
  public:
    void solve(int node,vector<vector<int>>& adj,vector<int> &vis,vector<int> &ans){
        vis[node]=1;
        ans.push_back(node);
        for(auto &it: adj[node]){
            if(vis[it]==0){
                solve(it,adj,vis,ans);
            }
        }
    }
    vector<int> dfs(vector<vector<int>>& adj) {
      
        int n=adj.size();
        vector<int> vis(n,0);
        vector<int> ans;
        int start=0;
        solve(start,adj,vis,ans);
        return ans;
    }
};


{ 

int main() {
    int tc;
    cin >> tc;
    cin.ignore();
    while (tc--) {
        int V;
        cin >> V;
        cin.ignore();
        vector<vector<int>> adj(
            V); // Use vector of vectors instead of array of vectors.

        for (int i = 0; i < V; i++) {
            string input;
            getline(cin, input);
            int num;
            vector<int> node;
            stringstream ss(input);
            while (ss >> num) {
                node.push_back(num);
            }
            adj[i] = node;
        }

        Solution obj;
        vector<int> ans = obj.dfs(adj);
        for (int i = 0; i < ans.size(); i++) {
            cout << ans[i] << " ";
        }
        cout << endl;
        cout << "~" << endl;
    }
    return 0;
}
```
  </p>
  </p>
</div>
