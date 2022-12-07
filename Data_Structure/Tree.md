# 트리 (Tree)
- **그래프**의 한 종류 (모든 트리는 그래프지만 모든 그래프가 트리는 아님)
- **방향** 그래프 (위에서 아래로의 방향만 존재, **계층적** 구조)
- **연결** 그래프 (모든 노드에 연결된 경로가 존재하지만 **단 한 개**씩만 존재)
- **비순환** 그래프 (사이클이 존재하지 않음)
- **노드**(**Node**)와 **간선**(**Edge**)으로 이루어져 있음
- 직계 상위 노드는 **부모 노드**, 직계 하위 노드는 **자식 노드**, 같은 부모 노드를 가진 노드는 **형제 노드**
- 부모 노드를 포함한 모든 상위 노드는 조상 노드, 자식 노드를 포함한 모든 하위 노드는 자손 노드
- 트리의 **가장 상위** 노드는 **루트 노드**, **가장 하위** 노드 (자식이 없는 노드) 는 **리프 노드**
- 노드의 개수가 N개일 때, **간선의 수**는 **N - 1**개
- **레벨**: 특정 노드까지 도달하는 **경로의 길이** (루트 노드의 레벨은 1)
- **높이**: 트리 안에서 어느 한 노드까지 도달하는 데 걸리는 **가장 긴 경로의 길이** (레벨 - 1)

## 순회 방법
- 트리를 **부모 노드**, **왼쪽 서브 트리**, **오른쪽 서브 트리** 세 부분으로 나누면서 순회
- 시간 복잡도는 모두 **O(N)**
### 전위 순회 (Preorder)
- **부모 -> 왼쪽 -> 오른쪽** 순서로 순회

|![image](https://user-images.githubusercontent.com/79434205/205824129-8950c79b-4cd9-4b9d-871a-03742548b146.png)|
|:---:|
|A - B - D - E - C - F - G|

### 중위 순회 (Inorder)
- **왼쪽 -> 부모 -> 오른쪽** 순서로 순회

|![image](https://user-images.githubusercontent.com/79434205/205824319-c79df23d-9af0-43df-8618-f0ccf144e3fb.png)|
|:---:|
|D - B - E - A - F - G - C|

### 후위 순회 (Postorder)|
- **왼쪽 -> 오른쪽 -> 부모** 순서로 순회

|![image](https://user-images.githubusercontent.com/79434205/205823613-20fe0844-1d77-4580-ad68-43525b712c27.png)|
|:---:|
|D - E - B - F - G - C - A|

## 탐색 방법
### 깊이 우선 탐색 (Depth First Search, DFS)
- **스택**(**Stack**)을 사용
1. 루트 노드를 push
2. 현재 노드의 처음 만나는 자식 노드를 push (push되는 자식의 순서는 전위, 중위, 후위 순회 중에 어떤 방법을 사용할지에 따라 달라짐)
3. 자식 노드가 없다면 pop하여 거슬러 올라가서 오른쪽 자식 노드를 push
4. 스택이 빌 때까지 반복
- 실제 구현 시에는 **재귀함수**를 사용하는 경우가 많기 때문에 무한 재귀가 되지 않도록 주의해야 함
- 찾고자 하는 노드가 **리프 노드에 가까운 경우**에 좋음

|C까지 가는 경우|F까지 가는 경우|
|:---:|:---:|
|![image](https://user-images.githubusercontent.com/79434205/205853985-753f3800-0dc5-4d8d-9a50-d5ecc8097474.png)|![image](https://user-images.githubusercontent.com/79434205/205856183-4a9f1406-a089-4a44-8a4c-e71e847370dc.png)|
|A - B - D - E - F - G - C|A - B - D - E - F|

### 너비 우선 탐색 (Breadth First Search, BFS)
- **큐**(**Queue**)를 사용
1. 루트 노드를 enqueue
2. 그 노드와 같은 레벨의 노드를 enqueue
3. 현재 노드의 자식 노드를 enqueue
4. dequeue 후 큐가 빌 때까지 반복
- DFS보다 **느린 편**
- 찾고자 하는 노드가 **루트 노드에 가까운 경우**에 좋음

|C까지 가는 경우|F까지 가는 경우|
|:---:|:---:|
|![image](https://user-images.githubusercontent.com/79434205/205854305-2f44a689-1d94-4c91-8c3b-8f8954ce08cb.png)|![image](https://user-images.githubusercontent.com/79434205/205854220-13fa7bf7-9764-4ba3-b65b-97869c2c8b7e.png)|
|A - B - C|A - B - C - D - E - F|

## 참고 사이트
- https://www.geeksforgeeks.org/introduction-to-tree-data-structure-and-algorithm-tutorials/
- https://www.geeksforgeeks.org/tree-traversals-inorder-preorder-and-postorder/
- https://www.geeksforgeeks.org/difference-between-bfs-and-dfs/
- https://www.programiz.com/dsa/trees