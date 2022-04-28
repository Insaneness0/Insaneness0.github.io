# Insaneness0.github.io
# 네트워크 유량
## 용어 정리
* Source: 유량의 시작점 
* Sink: 유량의 도착점
* Capacity: 용량
* Flow: 유량
* c(a,b):  a에서 b로 보낼 수 있는 용량
* f(a,b):  a에서 b로 흐르는 유량
## 개념 설명
1. 용량의 제한: 유량은 용량보다 항상 작거나 같다.
2. 유량의 대칭: 예를 들어 a에서 b로 유량의 흐르는 것과 b에서 a로 유량이 흐르는 것은 같은 것이다.
3. 유량의 보존: 들어오는 유량과 나가는 유량의 크기는 같다.
## DFS란??
### Depth First Search이고 한국어 표기로는 깊이 우선 탐색
* 트리나 그래프에서 한 가지의 루트로 탐색하는 중에 최대한 깊숙이 들어가서 확인 후 다시 돌아서 나와서 다른 루트를 탐색하는 방법이다.
## 유량 상쇄
* 기존에 존재하는 간선에 반대 방향인 간선을 추가해 음의 유량을 흘려보내는 것이다.
* 유량 상쇄는 추가적인 경로 탐색을 위해 하는 작업이다.
# Ford Fulkerson Algorithm
## 진행순서
1. 모든 간선을 0으로 초기화하고 반대 방향의 간선의 유량도 0으로 초기화한다.
2. Source에서 Sink로 갈 수 있는 경로를 DFS로 탐색한다.
3. 간선들의 남은 용량 중 가장 작은 유량을 보낸다.
4. 보낸 유량의 음의 값을 반대 방향 간선에도 보낸다.
5. 남은 용량이 있는 경로가 없을 때까지 계속 반복한다.
## Ex
<img width="80%" src="https://user-images.githubusercontent.com/101376892/165742192-edf6cb3f-5031-4250-9836-b0db800e006a.png"/>

1. 이 그림은 모든 간선과 반대 방향의 간선의 유량을 0으로 초기화한다
2. 깊이 우선 탐색 방법을 이용해 Source-> A -> B -> Sink 라는 경로를 탐색한다
3. 간선에 있는 가장 작은 유량 값인 1을 보낸다.
4. 반대 방향 간선에도 유량 상쇄를 이용해 마이너스 값의 유량을 보낸다.
<img width="80%" src="https://user-images.githubusercontent.com/101376892/165745369-d6a8c03a-7809-455f-9152-f18857177ddc.png">

5. Sourve -> B -> A -> Sink 라는 길의 남은 용량을 확인 후 가장 작은 값을 흘려 보낸다.
<img width="80%" src="https://user-images.githubusercontent.com/101376892/165745380-50856274-51d9-4255-84d1-bac8f11175cc.png"/>

6. 마지막에 (a,b)와 (b,a)가 상쇄되어 결과값이 나온다.
## 시간 복잡도
*  시간 복잡도 O(E*F)
* 시간 복잡도가 F와 관련이 있어 F값이 클수록 힘들어진다.
## 소스 코드
<img width="80%" src="https://user-images.githubusercontent.com/101376892/165749303-108d2832-c58d-4057-bf94-5aee3e2bf3a9.png"/>
<img width="80%" src="https://user-images.githubusercontent.com/101376892/165749305-688b9e47-772c-4e22-8181-cdefa8d95bd8.png"/>

### 소스코드 가져온 곳
https://grini25.tistory.com/172
