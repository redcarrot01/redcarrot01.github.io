---
title: 큐(Queue)
category: DataStructure
comments: true
order: 4
---

# 큐(Queue)의 성질
* __FIFO(First In First Out)__
* 원소의 추가가 O(1)
* 원소의 제거가 O(1)
* 제일 앞/뒤의 원소 확인이 O(1)
* 제일 앞/뒤가 아닌 나머지 원소들의 확인/변경이 원칙적으로 불가능
* __선형구조__ 의 자료구조이다.

## 배열을 이용한 큐 구현

```
// #include <bits/stdc++.h>
#include <iostream>

using namespace std;
#define ll long long

const int mx = 1000005;
int dat[mx];
int head = 0, tail = 0;

void push(int x) {
    dat[tail++] = x;
}

void pop() {
    head++;
}

int front() {
    return dat[head];
}
int back() {
    return dat[tail-1];
}

int main() {
    cin.tie(nullptr);
    ios::sync_with_stdio(false);
    push(1);
    push(2);
    push(3);

    cout << front();
    return 0;
}
```

# References
* [바킹독의 실전 알고리즘-0x06, 큐](https://www.youtube.com/watch?v=D_fwSy5tRAY)