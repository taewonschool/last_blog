---
layout: post
toc: true
title: 학교 커뮤니티 웹 애플리케이션
tags: [markdown, css, html, js ]
categories: Java
---

# 소셜 네트워크 프로젝트 



### 1.사용목적

```java
같은 지역의 고등학교 학생들끼리 교류를 높이고 그 교류를 기반하여
다양한 활동을 할 수 있도록 학생들에게 도움을 주기 위하여 만들어졌다.
또한 학생들끼리 교류하여 각 학교의 특징을 잘 살릴 수 있도록 도움을 준다.
```

### 2.기능

```java
회원가입:

사용자가 회원가입을 할 수 있습니다.
서버는 회원 정보를 JSON 파일에 저장합니다.
이메일 중복 확인 기능이 포함되어 있습니다.

로그인:

사용자가 로그인할 수 있습니다.
서버는 사용자의 자격 증명을 확인하고, JWT 토큰을 생성하여 쿠키에 저장합니다.
로그인 후 네비게이션 바에 추가적인 메뉴가 표시됩니다 (규칙, 포럼, 스터디 그룹, 마이 페이지, 로그아웃).

로그아웃:

사용자가 로그아웃할 수 있습니다.
서버는 쿠키를 지우고, 사용자를 처음 화면으로 리디렉션합니다.

마이 페이지:

사용자가 자신의 페이지에서 자기소개 글을 작성하고 저장할 수 있습니다.
자기소개 글은 JSON 파일에 저장됩니다.
마이 페이지에서는 현재 저장된 자기소개 글을 볼 수 있습니다.

스터디 그룹:

사용자는 스터디 그룹 목록을 조회할 수 있습니다.
새로운 스터디 그룹을 생성할 수 있습니다.
생성된 스터디 그룹 정보는 JSON 파일에 저장됩니다.
```

### 3.개발 내용

```java
개발 환경
프론트엔드: HTML, CSS, JavaScript, Bootstrap
백엔드: Node.js, Express
데이터베이스: JSON 파일을 사용하여 데이터 저장
인증: JWT (JSON Web Token)
기타: CORS 설정, dotenv 환경 변수 관리
주요 기능 및 구현 내용
1. 회원가입
사용자가 회원가입을 할 수 있으며, 이메일 중복 확인 기능이 포함되어 있습니다.

엔드포인트: POST /register
구현 내용:
클라이언트에서 사용자 정보 (이름, 이메일, 비밀번호)를 입력받아 서버로 전송.
서버는 JSON 파일에서 사용자 정보를 확인하고, 중복된 이메일이 없는 경우 새 사용자 정보를 추가.
성공 시 "Registration successful" 메시지 반환.

2. 로그인
사용자가 로그인할 수 있으며, 로그인 후 JWT 토큰이 발급됩니다.

엔드포인트: POST /login
구현 내용:
클라이언트에서 사용자 정보 (이메일, 비밀번호)를 입력받아 서버로 전송.
서버는 JSON 파일에서 사용자 정보를 확인하고, 일치하는 경우 JWT 토큰을 발급하여 쿠키에 저장.
성공 시 "Login successful" 메시지 반환.

3. 로그아웃
사용자가 로그아웃할 수 있으며, 로그아웃 후 쿠키가 삭제됩니다.

엔드포인트: POST /logout
구현 내용:
서버는 클라이언트에서 받은 요청에 대해 JWT 토큰 쿠키를 삭제.
성공 시 "Logout successful" 메시지 반환.

4. 마이 페이지
사용자가 자신의 마이 페이지에서 자기소개 글을 작성하고 저장할 수 있습니다.

엔드포인트:
GET /mypage: 사용자 정보 조회
POST /mypage/intro: 자기소개 글 저장
구현 내용:
GET /mypage: JWT 토큰을 확인하여 사용자 정보를 반환.
POST /mypage/intro: JWT 토큰을 확인하여 자기소개 글을 JSON 파일에 저장.

5. 스터디 그룹
사용자는 스터디 그룹을 생성하고 조회할 수 있습니다.

엔드포인트:
GET /study-groups: 스터디 그룹 목록 조회
POST /study-groups: 새로운 스터디 그룹 생성
구현 내용:
GET /study-groups: JSON 파일에서 스터디 그룹 목록을 반환.
POST /study-groups: 새로운 스터디 그룹 정보를 JSON 파일에 저장.
프론트엔드
index.html
네비게이션 바: 초기에는 홈, 회원가입, 로그인만 표시되고, 로그인 후 규칙, 포럼, 스터디 그룹, 마이 페이지, 로그아웃 항목이 추가로 표시됨.
로그인 상태 확인: 로그인 상태를 확인하여 네비게이션 바를 동적으로 변경.
login.html
로그인 폼: 사용자로부터 이메일과 비밀번호를 입력받아 서버로 전송.
로그인 성공 시: 메인 페이지로 리디렉션.
mypage.html
마이 페이지 폼: 사용자로부터 자기소개 글을 입력받아 서버로 전송.
자기소개 글 표시: 현재 저장된 자기소개 글을 표시.
백엔드
index.js
환경 설정: dotenv 패키지를 사용하여 환경 변수를 설정.
미들웨어: express, bodyParser, cookieParser, cors를 사용하여 서버를 설정.
JSON 파일 관리: 사용자 정보와 스터디 그룹 정보를 JSON 파일에 저장하고 불러옴.
CORS 설정: 클라이언트와 서버 간의 CORS 문제를 해결.
인증 및 JWT: JWT를 사용하여 사용자를 인증하고, 인증 미들웨어를 통해 보호된 엔드포인트에 접근할 수 있도록 함.
엔드포인트:
/login: 사용자 로그인 처리.
/register: 사용자 회원가입 처리.
/logout: 사용자 로그아웃 처리.
/mypage: 보호된 엔드포인트로, 로그인한 사용자의 정보를 반환.
/mypage/intro: 보호된 엔드포인트로, 사용자의 자기소개 글을 저장.
/study-groups: 스터디 그룹 목록 조회.
/study-groups: 새로운 스터디 그룹 생성.

```


### 4.개발중 오류

```java
1. 로그인 후 페이지 전환 오류
오류 설명: 사용자가 로그인 후 메인 페이지로 리디렉션되지 않음.

원인: 클라이언트에서 로그인 성공 후 window.location.href를 통해 페이지를 전환하려고 했으나, 조건문이 올바르게 설정되지 않음.

해결 방법:

login.html의 fetch 요청 성공 후 window.location.href = 'index.html';를 추가하여 로그인 성공 시 메인 페이지로 리디렉션되도록 수정.
javascript

.then(data => {
   if (data.message === 'Login successful') {
      alert('로그인 성공');
      window.location.href = 'index.html'; // 메인 페이지로 리디렉션
   } else {
      alert('이메일 또는 비밀번호가 잘못되었습니다.');
   }
})
2. CORS 정책 문제
오류 설명: 클라이언트에서 서버로 요청할 때 CORS 정책 위반으로 인해 요청이 차단됨.

원인: 서버의 CORS 설정이 잘못되어 클라이언트의 요청을 허용하지 않음.

해결 방법:

서버(index.js)에서 CORS 설정을 올바르게 구성하여 클라이언트의 요청을 허용함.
javascript

const corsOptions = {
    origin: 'http://localhost:3000', // 클라이언트 URL
    credentials: true, // 자격 증명을 허용합니다.
};
app.use(cors(corsOptions));
3. 인증 토큰 전달 문제
오류 설명: 인증된 사용자만 접근할 수 있는 페이지에 접근할 때 403 Forbidden 에러 발생.

원인: 클라이언트에서 서버로 요청할 때 인증 토큰이 제대로 전달되지 않음.

해결 방법:

클라이언트에서 fetch 요청 시 credentials: 'include'를 추가하여 쿠키가 포함되도록 설정.
javascript

fetch('http://localhost:3000/mypage', {
    method: 'GET',
    credentials: 'include' // 자격 증명을 포함한 요청 허용
})
4. JSON 파일 읽기/쓰기 문제
오류 설명: 사용자 정보나 스터디 그룹 정보를 JSON 파일에서 읽거나 쓸 때 오류 발생.

원인: JSON 파일이 존재하지 않거나 파일 경로가 잘못됨.

해결 방법:

JSON 파일이 존재하지 않는 경우 파일을 생성하고, 파일 경로를 올바르게 설정.
javascript

const readUsersFromFile = () => {
    if (!fs.existsSync(USERS_FILE)) {
        fs.writeFileSync(USERS_FILE, JSON.stringify([]));
    }
    const usersData = fs.readFileSync(USERS_FILE);
    return JSON.parse(usersData);
};
5. 서버 코드의 SyntaxError
오류 설명: 서버 코드 실행 시 SyntaxError 발생.

원인: 서버 코드가 예상치 않게 끝나거나, 중괄호 또는 소괄호가 닫히지 않음.

해결 방법:

전체 서버 코드를 점검하여 중괄호, 소괄호가 제대로 닫혔는지 확인하고, 코드의 끝부분이 올바르게 닫혔는지 확인.
6. 네비게이션 바 동적 변경 문제
오류 설명: 로그인 후에도 네비게이션 바가 동적으로 변경되지 않음.

원인: 로그인 상태 확인 로직이 제대로 작동하지 않음.

해결 방법:

클라이언트 코드에서 로그인 상태를 확인하는 로직을 수정하고, 로그인 상태에 따라 네비게이션 바를 동적으로 변경.
javascript

function checkLoginStatus() {
    fetch('http://localhost:3000/mypage', {
        method: 'GET',
        credentials: 'include'
    })
    .then(response => response.json())
    .then(data => {
        if (data.message) {
            document.getElementById('rulesLink').classList.remove('d-none');
            document.getElementById('studyGroupsLink').classList.remove('d-none');
            document.getElementById('forumLink').classList.remove('d-none');
            document.getElementById('mypageLink').classList.remove('d-none');
            document.getElementById('logoutLink').classList.remove('d-none');
            document.getElementById('registerLink').classList.add('d-none');
            document.getElementById('loginLink').classList.add('d-none');
        } else {
            document.getElementById('rulesLink').classList.add('d-none');
            document.getElementById('studyGroupsLink').classList.add('d-none');
            document.getElementById('forumLink').classList.add('d-none');
            document.getElementById('mypageLink').classList.add('d-none');
            document.getElementById('logoutLink').classList.add('d-none');
            document.getElementById('registerLink').classList.remove('d-none');
            document.getElementById('loginLink').classList.remove('d-none');
        }
    });
}
결론
이 프로젝트를 개발하면서 여러 가지 오류가 발생했지만, 각 오류의 원인을 분석하고 적절한 해결 방법을 적용하여 문제를 해결했습니다. 주요 오류는 CORS 정책 문제, 인증 토큰 전달 문제, JSON 파일 읽기/쓰기 문제, 네비게이션 바 동적 변경 문제 등이었으며, 이를 해결하여 최종적으로 안정적인 웹 애플리케이션을 개발할 수 있었습니다.







```
