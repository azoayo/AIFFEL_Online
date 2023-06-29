# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 김건
- 리뷰어 : 박영수

# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
  > 네, 코드가 정상적으로 작동하고 요구된 거북이 경로에 대한 표시 제대로 하였습니다.
- [X] 주석을 보고 작성자의 코드가 이해되었나요?
  > 네 주어진 코드를 보고 작성자의 코드가 이해되었습니다. 
- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 복수의길 표시에 대한 에러가 있지만 문제가 최적길을 요구하지 않았기 때문에 괜찮습니다.
- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 네 단순히 검색값을 붙힌것을 통해 해결한 것이 아닌 제대로 이해한것 같습니다.
- [X] 코드가 간결한가요?
  > 간결한것 같습니다. 다만 처음보는 알고리즘이라 비교는 어려울것 같습니다.

# 예시
1. 코드의 작동 방식을 주석으로 기록합니다.
2. 코드의 작동 방식에 대한 개선 방법을 주석으로 기록합니다.
3. 참고한 링크 및 ChatGPT 프롬프트 명령어가 있다면 주석으로 남겨주세요.

python
from ColabTurtle.Turtle import *

# 미로를 입력한다.
maze = [[0, 1, 0, 0, 0],
        [0, 0, 0, 1, 0],
        [0, 1, 1, 0, 0],
        [0, 0, 1, 1, 0],
        [0, 0, 0, 1, 0]]


# 출구 좌표값을 설정
def is_exit(x, y):
    return x == 4 and y == 4

# 미로 탐색 함수
def explore_maze(x, y):
    # 미로 밖의 좌표를 설정하는 경우 false 반환
    if x < 0 or y < 0 or x >= 5 or y >= 5:
        return False
    # 만약 벽이거나 지나온 길이면 false 반환
    if maze[x][y] == 1 or maze[x][y] == 2:
        return False
    # 출구좌표와 일치 한다면 True
    if is_exit(x, y):
        return True
    # x,y 값을 지나온 길로 설정
    maze[x][y] = 2

    #반복해서 상하좌우 좌표 함수로 들어
    if explore_maze(x + 1, y):
        seth(0)
        forward(20)
        return True

    if explore_maze(x - 1, y):
        seth(180)
        forward(20)
        return True

    if explore_maze(x, y + 1):
        seth(90)
        forward(20)
        return True

    if explore_maze(x, y - 1):
        seth(270)
        forward(20)
        return True

    # 회귀 종료
    maze[x][y] = 0
    return False

# 거북이 상태
initializeTurtle(initial_speed=10)
speed(5)
width(2)

#지나간 길 출력
def print_maze():
    for row in maze:
        print(row)

print("미로 탐색 시작")
# 미로 출력 값이 참이면 결과값 출력 거짓이면 메시지 출력
if explore_maze(0, 0):
    print("미로를 찾았습니다.")
    maze[4][4] = 2
    maze[0][0] = 0
    print("지나간 길:")
    print_maze()
else:
    print("미로를 찾을 수 없습니다.")


# 참고 링크 및 코드 개선

문제 범위에는 벗어나는 이야기지만
BFS / DFS 알고리즘을 통해 코드 개선이 가능합니다.
BFS : 너비 우선 탐색
DFS : 깊이 우선 탐색
https://cyc1am3n.github.io/2019/04/26/bfs_dfs_with_python.html
