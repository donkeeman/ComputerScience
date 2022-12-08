# AVL 트리 (AVL Tree)
- **균형 이진 탐색 트리**의 일종
- 노드에 **BF**(**Balance Factor**)라는 값을 부여
- BF는 **왼쪽 서브 트리의 BF - 오른쪽 서브 트리의 BF**로 결정 (가능한 값은 **-1**, **0**, **1**)
- **서브 트리가 없는 경우**는 그 부분의 BF를 **-1**로 취급하여 계산 (리프 노드의 BF는 자식이 없으므로 -1 - (-1) = 0)
- BF가 -1보다 작거나 1보다 클 경우 균형을 맞추기 위해 트리를 **회전**시킴

## LL (왼쪽 회전)
- 트리가 `/` 형태가 되었을 때 (Left-Skewed)
- 불균형이 일어난 노드를 그 자식 노드의 오른쪽 자식으로 보낸 후, 자식 노드였던 노드가 상위 노드가 되고, 자식 노드가 가지고 있던 오른쪽 서브 트리는 불균형이 일어난 노드의 왼쪽 서브 트리가 됨

    ![image](https://user-images.githubusercontent.com/79434205/206358066-84888183-dc2c-4082-a0d3-a5097787bae5.png)

## RR (오른쪽 회전)
- 트리가 `\` 형태가 되었을 때 (Right-Skewed)
- 불균형이 일어난 노드를 그 자식 노드의 왼쪽 자식으로 보낸 후, 자식 노드였던 노드가 상위 노드가 되고, 자식 노드가 가지고 있던 왼쪽 서브 트리는 불균형이 일어난 노드의 오른쪽 서브 트리가 됨

    ![image](https://user-images.githubusercontent.com/79434205/206357877-c627f48c-e761-4b88-8b57-97f66c435f1e.png)

## LR (왼쪽-오른쪽 회전)
- 트리가 `<` 형태가 되었을 때
- 오른쪽으로 꺾인 부분을 왼쪽으로 회전시켜서 트리를 `/` 형태로 만든 다음, RR과 동일한 과정을 거침

    ![image](https://user-images.githubusercontent.com/79434205/206363880-ecc9d6ed-55c8-4d0f-9019-4b454bb50a9c.png)

## RL (오른쪽-왼쪽 회전)
- 트리가 `>` 형태가 되었을 때
- 왼쪽으로 꺾인 부분을 오른쪽으로 회전시켜서 트리를 `\` 형태로 만든 다음, LL과 동일한 과정을 거침

    ![image](https://user-images.githubusercontent.com/79434205/206401700-eaa8b7bc-1812-4c8f-8b53-4937c28f073a.png)

## 연산
- 요소 삽입 ( **O(log N)** )
- 요소 제거 ( **O(log N)** )
- 요소 검색 ( **O(log N)** )

## 참고 사이트
- https://www.geeksforgeeks.org/insertion-in-an-avl-tree/
- https://www.programiz.com/dsa/avl-tree
