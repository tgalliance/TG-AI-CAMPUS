# TG에듀테크 AI 교육 플랫폼 - 사이트 2 (복사본)

> 📌 **이 사이트는 원본 사이트의 복사본입니다.**  
> 원본과 독립적으로 수정 및 운영 가능합니다.

---

## 🎯 프로젝트 개요

**프로젝트명**: TG에듀테크 AI 교육 플랫폼 (Site 2)  
**목적**: 공공기관, 기업을 위한 전문 AI 교육 및 컨설팅 플랫폼 (복사본)  
**복사일**: 2026-03-26

---

## 📂 파일 구조

```
site2/
├── index.html              # 메인 페이지
├── courses.html            # 강의 보기 페이지
├── recommended.html        # 추천 강의 페이지
├── consulting.html         # AI 컨설팅 서비스 페이지
├── dashboard.html          # 학습 현황 대시보드
├── login.html              # 로그인 페이지
├── mypage.html            # 마이페이지
├── support.html           # 고객지원
├── notices.html           # 공지사항
├── inquiry.html           # 교육문의
├── admin.html             # 관리자 페이지
├── admin-login.html       # 관리자 로그인
├── player.html            # 영상 플레이어
│
├── 📁 css/
│   ├── style.css           # 메인 스타일
│   ├── enhanced-styles.css # 향상된 스타일
│   ├── samsung-nav.css     # 네비게이션
│   ├── apple-style.css     # 애플 스타일 카드
│   ├── courses-custom.css  # 강의 페이지 커스텀
│   └── playlist-sidebar.css # 플레이리스트
│
└── 📁 js/
    ├── main.js             # 메인 스크립트
    ├── courses.js          # 강의 페이지 스크립트
    ├── courses-enhanced.js # 강의 향상 기능
    ├── storage.js          # 로컬 스토리지 관리
    ├── dashboard.js        # 대시보드 스크립트
    ├── search.js           # 검색 기능
    ├── admin.js            # 관리자 기능
    └── main-db.js          # 데이터베이스 연동
```

---

## ✅ 현재 구현된 기능

### 🎓 **교육 시스템**
- ✅ 강의 목록 표시 (courses.html)
- ✅ 추천 강의 페이지 (recommended.html)
- ✅ 영상 플레이어 (player.html)
- ✅ 강의별 북마크 기능
- ✅ 재생 속도 조절
- ✅ 노트 작성 기능
- ✅ 퀴즈 풀기
- ✅ 수강 후기 작성

### 👤 **사용자 시스템**
- ✅ 로그인/로그아웃 (localStorage 기반)
- ✅ 마이페이지 (학습 통계, 관심 강의)
- ✅ 학습 현황 대시보드 (진행률, 시청 시간)

### 💼 **AI 컨설팅 서비스**
- ✅ AI 컨설팅 소개 페이지 (consulting.html)
- ✅ 문제 공감 섹션 (4개 카드)
- ✅ 솔루션 제시
- ✅ 서비스 구성 안내
- ✅ Before/After 비교
- ✅ 활용 사례
- ✅ 차별화 포인트
- ✅ 프로세스 안내

### 🛠️ **고객 지원**
- ✅ 고객지원 (FAQ) - support.html
- ✅ 공지사항 - notices.html
- ✅ 교육문의 폼 - inquiry.html

### 🔧 **관리자 기능**
- ✅ 관리자 로그인 (admin-login.html)
- ✅ 관리자 대시보드 (admin.html)
- ✅ 강의 등록/수정/삭제
- ✅ FAQ 관리
- ✅ 공지사항 관리

---

## 🎨 주요 디자인 특징

- ✅ **메인 배너**: 영상/이미지 슬라이더 (점 클릭으로 전환)
- ✅ **Hero 타이틀**: "TG"와 "AI 교육 *컨설팅" 파란색 강조
- ✅ **텍스트 그림자**: 가독성을 위한 부드러운 그림자
- ✅ **GNB 메뉴**: 교육과정 | 추천강의 | 배움넷 | 도입사례 | 회사소개 | 학습현황 | AI컨설팅
- ✅ **푸터**: TG 건물 이미지 + 브랜드 정보
- ✅ **반응형 디자인**: 모바일/태블릿/데스크톱 대응

---

## 🌐 주요 페이지 URL

### **원본 사이트 (루트)**
- 메인: `/index.html`
- 강의: `/courses.html`
- 추천강의: `/recommended.html`
- AI 컨설팅: `/consulting.html`

### **복사본 사이트 (site2)**
- 메인: `/site2/index.html`
- 강의: `/site2/courses.html`
- 추천강의: `/site2/recommended.html`
- AI 컨설팅: `/site2/consulting.html`

---

## 📊 데이터베이스 (Genspark Table API)

### **테이블 구조**
```javascript
// courses 테이블
{
  id, title, description, instructor, 
  duration, thumbnail, level, category
}

// videos 테이블
{
  id, title, description, instructor,
  duration, thumbnail, videoUrl, courseId
}

// faqs 테이블
{
  id, question, answer, category, order
}

// notices 테이블
{
  id, title, content, date, important
}
```

---

## 🚀 다음 개발 계획

### **원본 vs 복사본 분리 계획**
- 🔲 원본: TG에듀테크 (기업용 AI 교육)
- 🔲 복사본: 용도에 맞게 커스터마이징 예정

### **추가 기능 계획**
- 🔲 YouTube 임베드 에러 수정
- 🔲 실제 영상 콘텐츠 교체
- 🔲 결제 시스템 연동
- 🔲 수료증 발급 기능
- 🔲 실시간 Q&A 채팅

---

## 🔧 기술 스택

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **UI Libraries**: Font Awesome, Google Fonts (Noto Sans KR)
- **Chart**: Chart.js (대시보드)
- **Storage**: localStorage (로그인 상태)
- **API**: Genspark RESTful Table API

---

## 📝 수정 이력

### **2026-03-26**
- ✅ 원본 프로젝트 복사 완료
- ✅ site2/ 폴더에 독립적인 사이트 구축
- ✅ 모든 HTML, CSS, JS 파일 복사 완료

---

## 📞 연락처

- **이메일**: info@ailearning.com
- **전화**: 02-1234-5678
- **주소**: 서울시 강남구

---

## 📌 중요 노트

⚠️ **이 사이트는 원본과 완전히 독립적입니다.**
- 원본 수정 → 복사본 영향 없음 ✅
- 복사본 수정 → 원본 영향 없음 ✅
- 각각 다른 도메인으로 배포 가능 ✅

---

**Made with ❤️ by TG에듀테크**
