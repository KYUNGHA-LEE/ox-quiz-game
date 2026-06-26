# 실시간 OX 퀴즈 게임

학생들이 각자 기기로 접속해 O 또는 X를 선택하고, 선생님은 `/admin` 화면에서 문제 진행과 정답 공개를 할 수 있는 실시간 OX 퀴즈 웹앱입니다.

## 프로젝트 개요

- 학생은 닉네임을 입력하고 O/X 답변을 제출합니다.
- 선생님은 관리자 화면에서 문제를 시작하고 정답을 공개합니다.
- 학생들의 응답은 Firebase Realtime Database를 통해 실시간으로 반영됩니다.
- 웹앱은 Vercel을 통해 배포합니다.

## 주요 기능

### 학생 화면 `/`

- 닉네임 입력
- 현재 문제 확인
- O / X 버튼 선택
- 답변 제출 완료 표시
- 정답 공개 후 맞음 / 틀림 확인

### 선생님 화면 `/admin`

- 현재 문제 확인
- 문제 시작
- 정답 공개
- 다음 문제로 이동
- 학생들의 O / X 응답 수 확인
- 실시간 참여 현황 확인

## 사용 기술

- Frontend: React 또는 Next.js
- Hosting: Vercel
- Database: Firebase Realtime Database
- Version Control: GitHub

## Firebase Realtime Database 구조

```json
{
  "game": {
    "status": "waiting",
    "currentQuestionId": "q1",
    "showAnswer": false
  },
  "questions": {
    "q1": {
      "text": "인터넷에 올린 글은 완전히 삭제하기 어렵다.",
      "answer": "O"
    },
    "q2": {
      "text": "비밀번호는 생일처럼 외우기 쉬운 것으로 만드는 것이 좋다.",
      "answer": "X"
    }
  },
  "students": {}
}
```

## 게임 상태

```text
waiting  : 대기 중
playing  : 문제 진행 중
revealed : 정답 공개
```

## 설치 방법

```bash
npm install
npm run dev
```

## Firebase 설정

Firebase 콘솔에서 웹앱을 등록한 뒤 Firebase 설정 값을 프로젝트에 연결해야 합니다.

필요한 값은 보통 다음과 같습니다.

```text
apiKey
authDomain
databaseURL
projectId
storageBucket
messagingSenderId
appId
```

Vercel 배포 시에는 프로젝트 설정의 Environment Variables에 Firebase 설정 값을 등록할 수 있습니다.

Vite 기반이면 환경변수 이름에 `VITE_` 접두사가 필요할 수 있고, Next.js 기반이면 `NEXT_PUBLIC_` 접두사가 필요할 수 있습니다.

## 배포 방법

1. GitHub에 프로젝트 코드를 업로드합니다.
2. Vercel에서 GitHub 저장소를 연결합니다.
3. 필요한 Firebase 환경변수를 Vercel에 등록합니다.
4. 배포를 실행합니다.
5. 배포된 주소에서 학생 화면과 선생님 화면을 확인합니다.

예시 주소:

```text
학생 화면: https://프로젝트주소.vercel.app/
선생님 화면: https://프로젝트주소.vercel.app/admin
```

## 주의 사항

`/admin` 주소를 사용하는 것만으로는 완전한 보안이 되지 않습니다.

학생이 `/admin` 주소를 알게 되면 관리자 화면에 접근할 수 있으므로, 실제 수업에서 사용하기 전에는 관리자 비밀번호 또는 로그인 기능을 추가하는 것이 좋습니다.

또한 Firebase Realtime Database를 잠금 모드로 만들었다면, 앱에서 읽기와 쓰기가 가능하도록 보안 규칙을 별도로 설정해야 합니다.

## 향후 개선 아이디어

- 관리자 비밀번호 기능
- 방 번호 기능
- 팀전 모드
- 문제 직접 추가 기능
- 점수 랭킹
- 제한 시간 타이머
- 정답자 목록 표시
- 수업별 문제 세트 저장

## 라이선스

수업 및 교육용으로 자유롭게 수정하여 사용할 수 있습니다.
