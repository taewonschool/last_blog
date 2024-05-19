---
layout: post
toc: true
title: 롤 프로젝트
tags: [markdown, css, html]
categories: Java
---

# 롤 프로젝트를 해보자

import java.util.Random;  
import java.util.Scanner;

### 1.픽창으로 넘어간뒤 포지션을 정해보자

```java
public class LolMatching {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        // 문제 1
        System.out.println("게임을 시작 하시겠습니까? 1)예, 2)아니오");
        int startGame = scanner.nextInt();

        if (startGame == 1) {
            System.out.println("예, 매칭을 시작하겠습니다.");

            // 랜덤으로 포지션 결정
            String[] positions = {"탑", "미드", "정글", "원딜", "서포터"};
            String fakerPosition = positions[random.nextInt(positions.length)];

            System.out.println("게임이 매칭되었습니다.");
            System.out.println("페이커님의 포지션은 " + fakerPosition + " 입니다.");
        } else {
            System.out.println("게임을 시작하지 않습니다.");
        }
```

### 2.선택한 게임과 지정된 포지션, 지정된 팀을 랜덤으로 나타내보자

```java
        // 문제 2
        System.out.println("게임을 시작 하시겠습니까? 1)예, 2)아니오");
        int startGame2 = scanner.nextInt();

        if (startGame2 == 1) {
            System.out.println("게임을 선택해주세요.");
            System.out.println("1.일반게임\n2.랭크게임\n3.우르프\n4.단일챔피언\n5.AI");

            int selectedGame = scanner.nextInt();
            String[] gameModes = {"일반게임", "랭크게임", "우르프", "단일챔피언", "AI"};

            System.out.println(gameModes[selectedGame - 1] + "을 선택했습니다. " + gameModes[selectedGame - 1] + "을 매칭을 하겠습니다…………………. ");

            // 랜덤으로 포지션과 팀 결정
            String[] teams = {"블루팀", "레드팀"};
            String selectedTeam = teams[random.nextInt(teams.length)];
            String selectedPosition = positions[random.nextInt(positions.length)];

            System.out.println("게임이 매칭되었습니다.");
            System.out.println("팀 진영은 " + selectedTeam + "입니다.");
            System.out.println("페이커님의 포지션은 " + selectedPosition);
        } else {
            System.out.println("게임을 시작하지 않습니다.");
        }
```

### 3.문제 1번 2번의 조건을 합쳐 팀의 위치, 파티원들의 포지션을 랜덤으로 나타내시오(*파티는 총 페이커를 포함 5명까지 가능하다,*파티 구성 인원이 4명 이하일 경우 외부인원의 포지션도 정해져야 한다.)

```java
        // 문제 3
        System.out.println("파티원의 수를 정해주세요 : ");
        int partySize = scanner.nextInt();

        if (partySize > 5) {
            partySize = 5;
        }

        String[] partyPositions = new String[partySize];
        for (int i = 0; i < partySize; i++) {
            partyPositions[i] = positions[random.nextInt(positions.length)];
        }

        System.out.println("게임을 선택해주세요.");
        System.out.println("1.일반게임\n2.랭크게임\n3.우르프\n4.단일챔피언\n5.AI");

        int selectedGame3 = scanner.nextInt();
        String selectedGameMode = gameModes[selectedGame3 - 1];

        System.out.println(selectedGameMode + "을 선택했습니다. " + selectedGameMode + "을 매칭을 하겠습니다…………………. ");

        // 랜덤으로 포지션과 팀 결정
        String selectedTeam3 = teams[random.nextInt(teams.length)];
        String selectedPosition3 = positions[random.nextInt(positions.length)];

        System.out.println("게임이 매칭되었습니다.");
        System.out.println("팀 진영은 " + selectedTeam3 + "입니다.");
        System.out.println("페이커님의 포지션은 " + selectedPosition3);
        for (int i = 0; i < partySize; i++) {
            System.out.println("파티원" + (i + 1) + "의 포지션은 " + partyPositions[i]);// 전과다른 파티원 추가
        }
```

### 4.문제 1,2,3 번의 조건을 만족하고 랜덤으로 매칭이 취소되고 4초뒤에 다시 매칭을 시작한다.

```java
        // 문제 4
        System.out.println(selectedTeam3 + "에서 누군가 게임을 취소해 다시 매칭을 시작합니다……");
        try {
            Thread.sleep(4000); // 4초
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // 4초 후 다시 매칭 시작
        System.out.println("......누군가 게임을 취소해 다시 매칭을 시작합니다.…..");
        // 이곳에서 다시 매칭 코드를 작성하면 됩니다.
        //에러해결
    }
}
```
