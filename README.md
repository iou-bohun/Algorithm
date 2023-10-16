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
  * 코드 정리
    1. 노드를 담을 Node 클래스 생성
    ```c#
     using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    [System.Serializable]
    public class Node
    {
        public Vector2Int coordinates;
        public bool isWalkable;
        public bool isExplored;
        public bool isPath;
        
        public Node(Vector2Int coordinates, bool isWalkable)
        {
            this.coordinates = coordinates;
            this.isWalkable = isWalkable;
        }
    }
    ```
    2. GridManager 스크립트
       * 그리드를 생성해준다.
         ``` c#
           void CreateGrid()
          {
            for(int x=0;x<gridSize.x;x++)
              {
                  for (int y=0;y<gridSize.y;y++)
              {
                  Vector2Int coordinates = new Vector2Int(x,y);
                  grid.Add(coordinates, new Node(coordinates,true));
                }
              }
          }
         
    3. BFS 알고리즘
       * 현제 노드의 주변을 탐색
         ``` c#
          void ExploreNeighbors()
         {
             List<Node> neighbors = new List<Node>();
             foreach(Vector2Int direction in directions)
             {
                 Vector2Int neighborCoordinates = currentSearchNode.coordinates + direction;
                 if (grid.ContainsKey(neighborCoordinates))
                 {
                     neighbors.Add(grid[neighborCoordinates]);
                 }
             }
         }
