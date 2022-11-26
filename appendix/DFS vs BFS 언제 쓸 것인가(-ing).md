# bfs vs dfs 언제 쓸 것인가? (-ing)

[https://stackoverflow.com/questions/3332947/what-are-the-practical-factors-to-consider-when-choosing-between-depth-first-sea](https://stackoverflow.com/questions/3332947/what-are-the-practical-factors-to-consider-when-choosing-between-depth-first-sea)

search tree의 구조, solution의 위치, 개수에 따라 달라진다.

- 만약 트리의 루트로부터 솔루션이 가깝다는 것을 안다면, bfs를 쓰는 것이 좋다
- 만약 트리가 매우 깊고, 솔루션이 적다면, bfs가 상대적으로 빠를 것이다. dfs는 엄청 오래 걸릴 수 있다.
- 만약 트리가 매우 넓다면 bfs를 사용하기 위해 많은 메모리가 들 것이므로, 완전 비효율적일 것이다.
- 만약 솔루션이 빈번하게 나오지만, 트리의 깊숙한 곳에 위치해 있다면 dfs가 더 좋다.
- 만약 서치 트리가 매우 깊자면, dfs의 서치 depth를 제한할 필요가 있다

dfs는 보통 게임에서 낼 수 있는 경우를 고려할 때에 쓰인다. (체스의 움직임을 시뮬레이션하는 등) 

bfs는 현재 노드에서 연결된 모든 노드를 탐색한다. 따라서 시작 노드에서 주어진 노드까지의 최단 경로를 구하는 데에 유용하다. 

서치할 노드가 얕다면(최초 노드로 부터 몇번 hop하면 닿을 수 있는 노드라면) bfs를 사용하는 것이 낫다.

만약, 서치할 노드가 깊다면, dfs를 쓰는 것이 낫다.

한번 풀어보자..

[https://leetcode.com/problems/01-matrix/](https://leetcode.com/problems/01-matrix/)