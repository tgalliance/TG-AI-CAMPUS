# 🚀 Cursor 개발자를 위한 이관 가이드

## 📋 프로젝트 개요
TG AI 캠퍼스 - AI 활용 교육 플랫폼  
현재 상태: **퍼블리싱 완료** (HTML/CSS/JS)  
필요 작업: **백엔드 기능 연동**

---

## ✅ 완성된 기능 (프론트엔드)

### 1. 메인 페이지 (index.html)
- ✅ 추천 매뉴얼 섹션 (6개 카드)
- ✅ GNB 네비게이션
- ✅ 반응형 디자인

### 2. 강좌 목록 페이지 (courses.html)
- ✅ 카테고리별 탭 (전체/기초/실전/직무별/고급)
- ✅ 14개 강좌 카드
- ✅ 유튜브 썸네일 자동 로딩
- ✅ course-player.html로 링크 연결

### 3. 강좌 상세 페이지 (course-player.html) ⭐ **핵심**
- ✅ Udemy 스타일 레이아웃
- ✅ 유튜브 썸네일 + 재생 버튼
- ✅ 4개 탭 (개요/커리큘럼/노트/Q&A)
- ✅ 사이드바 (강좌 정보 카드, 관련 강좌)
- ✅ 14개 강좌 데이터베이스 (coursesDB)
- ✅ URL 파라미터 기반 동적 로딩
- ✅ 반응형 디자인

### 4. 기타 페이지
- ✅ 18개 매뉴얼 페이지 (manual-*.html)
- ✅ 용어 사전 (dictionary.html)
- ✅ 학습 현황 (dashboard.html)
- ✅ 마이페이지 (mypage.html)
- ✅ 로그인 (login.html)
- ✅ 어드민 (admin.html)

---

## 🔧 Cursor에서 연동해야 할 기능

### 🎯 우선순위 1: 강좌 상세 페이지 백엔드 연동

#### 📍 위치: course-player.html

#### 1️⃣ **동영상 시청 기록** (진행률 추적)
```javascript
// 현재 코드 (line 948)
data-backend-integration="video-tracking"

// Cursor 작업:
// - 사용자 ID + 강좌 ID + 시청 시간 DB 저장
// - 진행률(%) 계산 및 업데이트
// - 사이드바 진행률 바 실시간 반영
```

**DB 테이블 설계 예시:**
```sql
CREATE TABLE learning_progress (
    id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    course_id INT,
    watch_duration INT,  -- 초 단위
    progress_percent DECIMAL(5,2),
    last_watched_at TIMESTAMP
);
```

---

#### 2️⃣ **노트 저장/불러오기 기능**
```javascript
// 현재 코드 (line 858, 974)
data-backend-integration="notes-system"
data-backend-integration="notes-crud"

// 현재: localStorage 임시 저장
// Cursor 작업:
// - saveNote() 함수를 API POST 요청으로 교체
// - loadNotes() 함수를 API GET 요청으로 교체
```

**API 엔드포인트:**
```javascript
// 노트 저장
POST /api/notes
{
  user_id: 123,
  course_id: 1,
  content: "강의 내용 메모...",
  timestamp: "2026-03-31 14:30"
}

// 노트 불러오기
GET /api/notes?user_id=123&course_id=1
```

**DB 테이블 설계 예시:**
```sql
CREATE TABLE course_notes (
    id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    course_id INT,
    content TEXT,
    created_at TIMESTAMP
);
```

---

#### 3️⃣ **Q&A 시스템**
```javascript
// 현재 코드 (line 858)
data-backend-integration="qa-system"

// Cursor 작업:
// - 질문 작성 폼 추가
// - 답변 등록 기능 (강사/관리자)
// - 댓글/대댓글 기능
```

**API 엔드포인트:**
```javascript
// 질문 작성
POST /api/qa/questions
{
  user_id: 123,
  course_id: 1,
  title: "질문 제목",
  content: "질문 내용..."
}

// 답변 작성
POST /api/qa/answers
{
  question_id: 456,
  user_id: 789, // 강사 ID
  content: "답변 내용..."
}
```

---

### 🎯 우선순위 2: 로그인 시스템

#### 📍 위치: login.html

#### 1️⃣ **사용자 인증**
```javascript
// Cursor 작업:
// - 이메일 + 비밀번호 인증
// - JWT 토큰 발급
// - 세션 관리
// - 비밀번호 해싱 (bcrypt)
```

**DB 테이블 설계 예시:**
```sql
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    email VARCHAR(100) UNIQUE,
    password VARCHAR(255),  -- bcrypt hashed
    name VARCHAR(50),
    department VARCHAR(50),
    created_at TIMESTAMP
);
```

---

### 🎯 우선순위 3: 학습 현황 페이지

#### 📍 위치: dashboard.html

#### 1️⃣ **내가 본 강좌/매뉴얼 목록**
```javascript
// Cursor 작업:
// - 사용자별 학습 기록 조회
// - 진행률 표시
// - 최근 본 강좌 순으로 정렬
```

**API 엔드포인트:**
```javascript
GET /api/users/{user_id}/learning-history
// 응답:
[
  {
    course_id: 1,
    title: "AI 기초 완전 정복",
    progress: 45,
    last_watched: "2026-03-30"
  },
  ...
]
```

---

### 🎯 우선순위 4: 마이페이지

#### 📍 위치: mypage.html

#### 1️⃣ **비밀번호 변경**
```javascript
// Cursor 작업:
// - 현재 비밀번호 확인
// - 새 비밀번호 유효성 검사
// - bcrypt 해싱 후 DB 업데이트
```

#### 2️⃣ **내 노트 모아보기**
```javascript
GET /api/users/{user_id}/notes
```

---

### 🎯 우선순위 5: 어드민 페이지

#### 📍 위치: admin.html

#### 1️⃣ **사용자 관리**
- 100명 직원 계정 일괄 등록
- 비밀번호 초기화
- 학습 통계 조회

#### 2️⃣ **강좌 관리**
- 강좌 추가/수정/삭제
- 유튜브 영상 URL 관리

---

## 📊 강좌 데이터 구조

### coursesDB (course-player.html line 948)
14개 강좌 데이터가 JavaScript 객체로 저장되어 있습니다.

**Cursor 작업:**
1. 이 데이터를 MySQL/PostgreSQL DB로 이관
2. GET API로 동적 로딩

**DB 테이블 설계 예시:**
```sql
CREATE TABLE courses (
    id INT PRIMARY KEY,
    title VARCHAR(200),
    video_id VARCHAR(20),  -- 유튜브 비디오 ID
    instructor VARCHAR(100),
    duration VARCHAR(20),
    level VARCHAR(20),
    rating DECIMAL(2,1),
    students INT,
    description TEXT
);

CREATE TABLE course_objectives (
    id INT PRIMARY KEY AUTO_INCREMENT,
    course_id INT,
    objective TEXT
);

CREATE TABLE course_curriculum (
    id INT PRIMARY KEY AUTO_INCREMENT,
    course_id INT,
    title VARCHAR(200),
    duration VARCHAR(20),
    sequence INT
);
```

---

## 🎨 CSS 경로 주의사항

### 절대경로 사용 중 (안전)
모든 CSS/JS 파일이 상대경로로 작성되어 있어 이관 시 깨지지 않습니다.

```html
<link rel="stylesheet" href="css/style.css">
<link rel="stylesheet" href="css/samsung-nav.css?v=3">
<script src="js/main.js"></script>
```

### 이미지 경로
```html
<img src="images/logo.png">
<img src="https://img.youtube.com/vi/{video_id}/maxresdefault.jpg">
```

---

## 🔐 보안 체크리스트

### ✅ 구현 필수
- [ ] bcrypt 비밀번호 해싱
- [ ] JWT 토큰 인증
- [ ] SQL Injection 방지 (Prepared Statements)
- [ ] XSS 방지 (입력값 검증)
- [ ] CSRF 토큰
- [ ] HTTPS 적용 (배포 시)

---

## 🚀 배포 가이드

### 1. Cafe24 호스팅 배포
1. 모든 HTML/CSS/JS 파일 업로드
2. Node.js + Express 백엔드 설정
3. MySQL 데이터베이스 생성
4. 환경 변수 설정 (.env)
5. PM2로 Node.js 프로세스 관리

### 2. 회사 서버 배포
1. Linux 서버 준비 (Ubuntu 22.04 권장)
2. Nginx 리버스 프록시 설정
3. SSL 인증서 설치 (Let's Encrypt)
4. 도메인 연결

---

## 📞 개발 시 참고사항

### 🎯 프론트엔드 완성도: 95%
- 디자인 완료
- 반응형 완료
- UI/UX 완료
- 더미 데이터 연동 완료

### 🔧 백엔드 필요 작업: 5일 예상
- Day 1: DB 설계 + 사용자 인증
- Day 2: 강좌 CRUD API
- Day 3: 학습 기록 + 노트 API
- Day 4: Q&A + 어드민
- Day 5: 테스트 + 배포

---

## 🎁 추가 제공 파일

### 1. README.md
프로젝트 전체 문서

### 2. 모든 HTML 파일 (26개)
- index.html
- courses.html
- course-player.html ⭐
- 18개 manual-*.html
- dashboard.html
- mypage.html
- login.html
- admin.html
- 기타 페이지들

### 3. CSS 파일
- css/style.css
- css/samsung-nav.css

### 4. 이미지 폴더
- images/ (로고, 아이콘 등)

---

## 💡 개발 팁

### 유튜브 썸네일 URL
```javascript
// 고화질 썸네일
https://img.youtube.com/vi/{video_id}/maxresdefault.jpg

// 중화질 썸네일 (fallback)
https://img.youtube.com/vi/{video_id}/hqdefault.jpg
```

### URL 파라미터 예시
```
course-player.html?id=1&video=kDGca4w8i6Q
                    ↑           ↑
                 강좌 ID    유튜브 ID
```

### 로컬스토리지 임시 데이터
```javascript
// 노트 데이터
localStorage.getItem('courseNotes')

// 이 데이터를 DB로 마이그레이션하세요
```

---

## 🎓 강좌 ID 매핑표

| ID | 강좌명 | 유튜브 ID | 난이도 |
|----|--------|-----------|--------|
| 1 | AI 기초 완전 정복 | kDGca4w8i6Q | 초급 |
| 2 | ChatGPT 200% 활용법 | JMUxmLyrhSk | 초급 |
| 3 | 2026 AI 최신 트렌드 | BLkWR4VrqzI | 전체 |
| 4 | 프롬프트 엔지니어링 마스터 | Cn-vCT-Ht4Q | 중급 |
| 5 | AI 업무 자동화 실전 | 1OaMKEWvwCs | 중급 |
| 6 | 생성형 AI 완전 정복 | klNLewDIr6M | 중급 |
| 7 | 마케팅 실무 AI 활용 | 7yGALz5P4tY | 초급 |
| 8 | 개발자를 위한 AI 코딩 | mBjPyte2ZZo | 중급 |
| 9 | HR 업무 AI 혁신 | PjE-z5_QZxc | 초급 |
| 10 | 재무·회계 AI 실무 | YVWXgvbMeys | 중급 |
| 11 | 기획·전략 AI 활용 | sTeoEFzVNSc | 중급 |
| 12 | AI 워크플로우 구축 | jacBgJIso_0 | 고급 |
| 13 | AI 에이전트 활용법 | MLBaYdIb7SY | 고급 |
| 14 | 팀 AI 협업 전략 | KjJa6Y-3nFs | 고급 |

---

## ✨ 완료 후 확인사항

### 프론트엔드 테스트
- [ ] courses.html → 강좌 카드 클릭
- [ ] course-player.html 정상 로딩
- [ ] URL 파라미터 변경 시 강좌 정보 변경 확인
- [ ] 유튜브 썸네일 로딩 확인
- [ ] 재생 버튼 클릭 시 유튜브 새 탭 열림

### 백엔드 연동 후 테스트
- [ ] 로그인/로그아웃
- [ ] 학습 진행률 업데이트
- [ ] 노트 저장/불러오기
- [ ] Q&A 작성/답변
- [ ] 어드민 페이지 기능

---

## 📧 문의사항
프론트엔드 관련 문의: Genspark AI Agent  
백엔드 개발: Cursor AI Agent

**화이팅! 🚀**
