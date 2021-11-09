---
layout: post
title: "Bit Library"
---

---

{% include carousel.html height="50" unit="%" duration="7" %}
**개발기간 　　 ┃** 2021.04.29 - 2021.05.06

**개발인원 　　 ┃** 2명

**프로젝트 개요 ┃** 도서 대출/반납 및 열람실 예약 서비스. 콘솔창에 구현

**개발도구 　　 ┃** Eclipse, SQL Developer

**담당한 기능　　**

1. 관리자
   - 열람실 등록, 사회적 거리두기모드
   - 도서 등록
1. 열람실
   - 좌석 조회
   - 좌석 예약, 연장, 취소

---

#### 열람실 좌석표 구현

![reservation](/assets/img/projects/proj-1/bit1.png)
사회적 거리두기 모드 적용 시▼
![socialdistance](/assets/img/projects/proj-1/socialdistance.png)
짝수열이 예약 불가능 상태로 바뀐다.

#### 💡 좌석 조회를 빠르게

처음엔 좌석을 조회할 때, **한 좌석의 예약 상태를 각각 읽고 하나씩 표시하는 방식**을 사용하였다. 그랬더니 속도가 너무 느려 사용성이 떨어진다는 판단이 들어 조회 방법을 바꿔보았다. :

```java
	for (int i = 0; i < rowCount; i++) {
			char row = (char) ('A' + i);
			System.out.print("          ");
			System.out.print(row + ": ");
			for (int j : 한 행의 예약상태 배열) {
				if (j == 1) {
					System.out.print("■ ");
				} else {
					System.out.print("□ ");
				}
			}
			System.out.println();
		}
```

위와 같이 좌석들의 **예약 상태를 한 행씩 불러와 (ex. A행에 속하는 모든 좌석 A1, A2, A3, ... A8의 예약상태를 한 번에 읽음) 그것을 배열에 저장**하고, 배열에 저장된 값들을 for문을 통해 불러와 표시를하니 좌석 조회 속도가 눈에 띄게 향상되었다.

#### 💡 콘솔창에서 로그인 유지

서블릿이나 스프링을 사용한 웹개발에서 로그인 유지는 주로 session을 통해 이루어진다. 콘솔창에서는 어떻게 유지를 해야할지 고민하다가, **아이디를 저장하는 class를 따로 생성하고 로그인 시 myId라는 변수에 저장**하는 방식을 생각해냈다.

이미 로그인을 한 상태라면 아이디가 필요한 영역에서 새로 아이디 입력을 요구하지 않고, myId에 저장된 값을 불러와 사용하는 식이다. 로그아웃 시, myId는 null으로 설정된다.

#### 💡 DB ERD

## ![Database](/assets/img/projects/proj-1/bit-db.png)

---

**깃헙주소 　　 ┃** [https://github.com/Dayook/bitLibrary](https://github.com/Dayook/bitLibrary){:target="\_blank"}

### EPILOGUE

콘솔창 화면 구현으로 첫 프로젝트를 시작했습니다. 기능도 많지 않고 투박해보이지만 나름대로 고심하며 만들었던 기억이 납니다.

이 때, 깃헙 사용법을 잘 몰라서 카톡으로 코드를 주고받기도 했는데요. 깃헙 사용법을 확실히 익혀둬야겠다고 다짐한 계기가 되어준 프로젝트였기도 합니다.

---
