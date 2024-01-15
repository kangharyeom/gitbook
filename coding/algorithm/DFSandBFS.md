# 깊이 우선 탐색(DFS)과 너비 우선 탐색(BFS)

깊이 우선 탐색(DFS)과 너비 우선 탐색(BFS) 그래프를 탐색하는 방법을 대표하는 두 가지 방법입니다.
그래프는 정점(node)과 정점 사이를 연결하는 간선(edge)로 이루어져 있으며 '탐색'은 차례대로 모든 정점을 한번씩 방문하는 것을 뜻합니다.

## 깊이 우선 탐색 (DFS, Depth-First Search)
![DFS](../../assets/Depth-First-Search.gif)

루트 노드에서 시작해서 다음 분기(branch)로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방식을 말합니다.

### DFS의 특징
- 모든 노드를 방문하고자 하는 경우에 활용합니다.
- 깊이 우선 탐색(DFS)이 너비 우선 탐색(BFS)보다 좀 더 간단합니다.
- 검색 속도는 너비 우선 탐색(BFS)이 더 빠릅니다.

## 너비 우선 탐색 (BFS, Breadth-First Search)
![BFS](../../assets/Breadth-First-Search-Algorithm.gif)

루트 노드에서 시작해서 인접한 노드를 먼저 탐색하는 방법입니다.
시작 정점애서 가까운 정점을 먼저 방문하고 멀리 있는 정점을 나중에 방문하는 순회 방법입니다.

### BFS의 특징
- 주로 두 노드의 최단 경로를 찾을 때 활용합니다.

## 깊이 우선 탐색 (DFS)과 너비 우선 탐색 (BFS) 비교

| 깊이 우선 탐색 (DFS) | 너비 우선 탐색 (BFS)  |
|:--------------:|:---------------:|
|  스택 또는 재귀 함수   |        큐        |
|  최적해라는 보장 없음   |    항상 최적해 보장    |
| 그래프 규모가 클 때 사용 | 그래프 규모가 작을 때 사용 |
| 특정 목표 노드를 찾을 때 |   최단 경로를 찾을 때   |

### 깊이 우선 탐색 (DFS)과 너비 우선 탐색 (BFS) 시간 복잡도
깊이 우선 탐색 (DFS)과 너비 우선 탐색 (BFS) 모두 시간복잡도는 동일합니다. 

``` markdown
 인접 리스트 : O(N+E)  
 인접 행렬   : O(N^2)  
```


## 깊이 우선 탐색 (DFS) 알고리즘
### 재귀
```java
static Stack<Integer> stack = new Stack<>();
static StringBuilder sb = new StringBuilder();
static boolean node[][] = new boolean[n+1][n+1], visited[] = new boolean[n+1];
static void dfs(int v) {
        if(visited[v])
        return;
        sb.append(v+" ");
        for(int i=1; i<=n; i++)
        if(node[v][i] && !visited[i]) {
        visited[i] = true;
        dfs(i);
    }
}
```
### 스택
```java
public static String dfs(int v, boolean node[][]) {
        StringBuilder sb = new StringBuilder();
        Stack<Integer> stack = new Stack<>();
        boolean visited[] = new boolean[n+1];
        stack.add(v);
        int idx;
        while(!stack.isEmpty()) {
        idx = stack.pop();
        if(visited[idx])
        continue;
        visited[idx] = true;
        sb.append(idx+" ");
        for(int i=0; i<n; i++)
        if(node[idx][i] && !visited[i])
        stack.add(i);
    }
    return sb.toString();
}
```

## 너비 우선 탐색 (BFS) 알고리즘
### 큐
```java
static boolean[] visit;
//연결 리스트, 행렬 그래프 중 선택
static LinkedList<Integer>[] graph;
static int[][] graph;

// 시작 정점 v
public static void bfs(int v) {
            Queue<Integer> queue = new LinkedList<>();
            queue.add(v); //시작 정점 큐에 넣기
            visit[v] = true; //시작 정점 방문
    
            while(!queue.isEmpty()) {
            int temp = queue.poll();
            System.out.println(temp);
    
            for(int nextV : graph[temp]) {
            if(!visit[nextV]) {
            queue.add(nextV);
            visit[nextV] = true;
            }
        }
    }
}
```
