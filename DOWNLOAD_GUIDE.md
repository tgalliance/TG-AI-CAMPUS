# TG AI 캠퍼스 - 다운로드 가이드

## 📥 다운로드 방법

### 1단계: 파일 다운로드
이 프로젝트의 모든 파일을 다운로드하려면:

**현재 GenSpark 화면에서:**
1. 브라우저 주소창의 URL을 확인하세요
2. 프로젝트 ID를 복사하세요 (예: 92857f6c-224c-4aee-84f1-787c80fe304f)

### 2단계: 로컬 실행
1. 모든 파일을 한 폴더에 저장
2. `index.html` 파일을 더블클릭
3. 브라우저에서 자동으로 열립니다

### 3단계: 서버 업로드 (카페24 등)
1. FTP 프로그램 설치 (FileZilla 권장)
2. 서버 접속 후 `/www` 또는 `/public_html`에 업로드
3. 모든 폴더 구조를 그대로 유지하세요

## 📁 필수 파일 목록

### HTML 페이지 (메인)
- `index.html` - 메인 페이지 ⭐
- `dashboard.html` - 학습현황
- `courses.html` - 강좌보기
- `about.html` - 소개
- `programs.html` - 강좌소개
- `manuals.html` - AI 활용 메뉴얼
- `dictionary.html` - AI 용어 사전
- `support.html` - 학습 도우미
- `notices.html` - 공지사항
- `inquiry.html` - 강의문의
- `recommended.html` - 추천강의

### CSS 폴더
- `css/style.css` - 메인 스타일
- `css/samsung-nav.css` - 네비게이션
- `css/enhanced-styles.css` - 추가 스타일
- `css/apple-style.css` - 애플 스타일

### 이미지 폴더
- `images/` - 모든 이미지 파일

### site2 폴더
- `site2/` - 서브 사이트 (TG 에듀테크)

## ⚠️ 중요 사항

**반드시 지켜야 할 것:**
1. 폴더 구조를 그대로 유지하세요
2. 모든 파일을 함께 업로드하세요
3. index.html이 루트(최상위) 폴더에 있어야 합니다

**폴더 구조:**
```
프로젝트폴더/
├── index.html
├── dashboard.html
├── courses.html
├── css/
│   ├── style.css
│   └── ...
├── images/
│   └── ...
├── js/
│   └── ...
└── site2/
    └── ...
```

## 🌐 서버 업로드 방법

### FileZilla 사용법:
1. FileZilla 다운로드: https://filezilla-project.org/
2. 실행 후 FTP 정보 입력:
   - 호스트: ftp.도메인.com
   - 사용자명: FTP ID
   - 비밀번호: FTP PW
   - 포트: 21
3. 왼쪽(로컬) → 오른쪽(서버)로 드래그
4. 완료!

## 💻 로컬 테스트 서버 (선택사항)

더 정확한 테스트를 원하시면:

**Python 있는 경우:**
```bash
python -m http.server 8000
```

**VS Code 사용:**
- Live Server 확장 프로그램 설치
- index.html 우클릭 → Open with Live Server

## 🆘 문제 해결

**Q: 디자인이 깨져요**
- CSS 폴더가 index.html과 같은 위치에 있는지 확인

**Q: 이미지가 안 보여요**
- images 폴더가 있는지 확인

**Q: 메뉴 클릭이 안 돼요**
- 로컬에서는 정상. 서버 업로드 후 확인

---

작업일: 2026-03-30
프로젝트: TG AI 캠퍼스 (TG Alliance 전사 AI 교육 플랫폼)
