
# 레드-블랙 트리 (Red-Black Tree)
- **균형 이진 탐색 트리**의 일종
- 노드에 **red, black 중 하나의 값**을 부여
- **루트 노드**는 무조건 **black**
- **리프 노드**들은 무조건 **black**  
(모든 리프 노드를 항상 black으로 유지하기 위해서, **아무 값을 가지지 않는 black 노드** (**NIL**) 를 실제 리프 노드의 자식으로 가지게 함)
- **red 노드의 자식 노드**는 무조건 **black** (red는 연속으로 올 수 없음)
- 루트에서 리프 노드까지 가는 경로에서 만나는 black 노드들의 개수 (**Black Depth**) 는 모두 같음
- 요소 삽입 시에는 기본적으로 **red 노드로 삽입**
- red 노드의 부모가 red 노드인 경우 (**Double Red**) 가 발생하면 **Restructuring** 또는 **Recoloring** 을 통해 균형을 맞춤 (부모 노드의 형제 노드 (**삼촌 노드**)의 **색**에 따라 결정)

## Restructuring
- 현재 노드와 그 부모 노드가 red일 때, **삼촌 노드**가 **black**인 경우
- 노드의 색은 바꾸지 않고 **위치**만 바꾸는 과정
- 현재 노드, 부모 노드, 조부모 노드 이 3개를 오름차순으로 정렬 후, 중앙값을 가진 노드를 부모 및 black 노드로 만들고 나머지 두 개를 각각 자식 및 red 노드로 만들어 줌
- black 노드의 개수가 바뀌는 것은 아니므로 **Black Depth에는 영향을 끼치지 않음**
- 시간 복잡도는 **O(1)**

    ![image](https://user-images.githubusercontent.com/79434205/206439603-1dbfa4ec-f90b-415c-8ed6-8cdb92acfe4c.png)

## Recoloring
- 현재 노드와 그 부모 노드가 red일 때, **삼촌 노드**도 **red**인 경우
- 노드의 위치는 바꾸지 않고 **색**만 바꾸는 과정
- 부모 노드와 삼촌 노드를 black 노드로, 조부모 노드를 red 노드로 변경
- 실행 후 상위에 Double Red가 또 발생할 수도 있음 -> **해결될 때까지** 거슬러 올라가면서 Recoloring **반복**
- 시간 복잡도는 **O(log N)**

    ![image](https://user-images.githubusercontent.com/79434205/206461360-e04680dd-88b0-4af4-abe9-dfffe4960861.png)

## 연산
- 요소 삽입 ( **O(log N)** )
- 요소 제거 ( **O(log N)** )
- 요소 검색 ( **O(log N)** )

## 참고 사이트
- https://www.geeksforgeeks.org/introduction-to-red-black-tree/
- https://www.programiz.com/dsa/red-black-tree
