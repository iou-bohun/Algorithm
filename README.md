# Algorithm
## Path Finding 알고리즘
  1. Breadth First Search (BFS) 
  2. Dijkstra
  3. A*

|알고리즘|항상 짧은길|이동 비용|다수의 시작점과 끝점|속도|
|------|---|---|---|---|
|BFS|O|X|O|중간|중간|
|Dijkstra|O|O|O|느림|
|a*|X|O|O|빠름|

 ## Breadth First Search 
  * 탬색 원리
    1. 탐색 방향 정하기
    2. 현제 노드를 트리에 Add
    3. 이웃 노드를 1에서 정한 탐색 방향 순서대로 Add
    4. 다음 트리로 이동
    5. 목적지가 아니면 3부터 다시 시작
    6. 목적지에 도달하면 첫 노드까지 되돌아가며 기록
    7. 기록한 노드들 반전
  
