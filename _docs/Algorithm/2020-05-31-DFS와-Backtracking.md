---
title: "DFS와 Backtracking(백트래킹)"
category: Algorithm
date: 2020-05-31 17:03:47
comments: true
order: 2
---

## 백트래킹

- 해를 찾는 도중 해가 아니어서 막히면, 되돌아가서 다시 해를 찾아가는 기법
- 최적화 문제, 결정 문제 푸는 방법

#### DFS와 백트래킹

**DFS**

- 가능한 모든 경로 탐색

- N! 가지의 경우의 수 문제는 처리 불가

**백트래킹**

- 지금의 경로가 해가 될 것 같지 않으면 되돌아 감

- 가지 치기 라고 부름

- 모든 경우의 수 중 특정한 조건을 만족하는 경우만 살펴보는 것



## N-Queen 문제 - 백준 9663번

- 백트래킹에서 자주 등장하는 문제

- n*n 안에 n개의 퀸을 배치하는 문제, 퀸들은 자신의 일직선상 및 대각선상에 아무 것도 놓이면 안됨

  

![image](https://user-images.githubusercontent.com/38436013/112236486-f7be9980-8c83-11eb-91f6-cab97ed6e179.png)
![image](https://user-images.githubusercontent.com/38436013/109910090-b1ac9080-7cea-11eb-98cf-bbbecb7616bd.png)

- 입력 : N (1~15)

- 출력 : N개를 서로 공격 못하게 놓는 경우의 수

- SOLVE

  일차원 배열 이용하여 해결 가능,  그이유는 퀸의 열 위치가 서로 같게 배치될 수 없기 때문이다(일직선상 배치 못)

  ![image](https://user-images.githubusercontent.com/38436013/109910343-3dbeb800-7ceb-11eb-8633-61ace0fec7cd.png)

  대각선 배치의 경우, 

  ![image](https://user-images.githubusercontent.com/38436013/109910300-267fca80-7ceb-11eb-91d0-e76f1fedab21.png)

#### 코드

~~~
# include <stdio.h>
# include <iostream>

int cnt = 0;
int n;
int board[15];

// 유망한지 판단하는 함수
int promising(int cdx) {

	// 같은 열이면 안되고, 대각선상에 있어서도 안 된다
	for (int i = 0; i < cdx; i++) { // 대각선상 : cdx 행 - 앞 행 == cdx 열 -  앞 행의 열
		if (board[cdx] == board[i] || cdx - i == abs(board[cdx] - board[i]))
			return 0;
	}	
	return 1;
}
// 백트래킹 알고리즘 수행
void nqueen(int cdx) {

	// cdx가 마지막 행까지 수행하고 여기까지 오면 찾기 완료
	if (cdx == n)
	{
		cnt++;
		return;
	}
	for (int i = 0; i < n; i++) {
		board[cdx] = i;  //cdx번째 행, i번째 열에 퀸을 놓아본다
		// 이후 그 행에 둔 것에 대한 유망성 판단
		if (promising(cdx)) // 그자리에 두어도 오케이라면
			nqueen(cdx + 1); // 그 다음행에 퀸 놓기 시도

	}

}
int main() {
	scanf_s("%d", &n);
	nqueen(0);
	printf("%d", cnt);
}

~~~



#### 참고했습니다.

[n-queen 설명 및 그림 출처](https://chanhuiseok.github.io/posts/baek-1/)