# Templater 플러그인 가이드

> 동적 템플릿으로 노트 생성 자동화

**카테고리**: 생산성 & 자동화
**난이도**: 높음
**추천도**: ⭐⭐⭐⭐⭐

---

## 📋 개요

### **Templater란?**
변수, 함수, JavaScript를 사용하여 동적 템플립을 생성하고 노트 생성을 자동화하는 플러그인

### **주요 기능**
- ✅ 동적 템플릿
- ✅ 변수 삽입
- ✅ 조건문/반복문
- ✅ JavaScript 실행
- ✅ 폴더 템플릿
- ✅ 시스템 명령어 실행

---

## 🚀 설치 & 설정

### **1. 설치**
```
Settings → Community plugins → Browse
검색: "Templater"
Install → Enable
```

### **2. 기본 설정**
```
Settings → Templater
- Template folder location: "Templates"
- Automatic jump to cursor: ON
- Trigger Templater on new file creation: ON
```

---

## 🎨 기본 문법

### **1. 변수**
```markdown
<% tp.date.now("YYYY-MM-DD") %>
<% tp.file.title %>
<% tp.file.folder() %>
<% tp.user.name %> (커스텀 변수)
```

### **2. 날짜 함수**
```markdown
<% tp.date.now("YYYY-MM-DD HH:mm") %>
<% tp.date.tomorrow("YYYY-MM-DD") %>
<% tp.date.yesterday("YYYY-MM-DD") %>
<% tp.date.weekday("YYYY-MM-DD", 0) %> (일요일)
```

### **3. 파일 함수**
```markdown
<% tp.file.title %>
<% tp.file.path() %>
<% tp.file.folder() %>
<% tp.file.selection() %>
```

---

## ⚡ 고급 기능

### **1. 조건문**
```markdown
<%* if (tp.file.title.includes("데일리")) { %>
# 데일리 노트
<%* } else { %>
# 일반 노트
<%* } %>
```

### **2. 반복문**
```markdown
<%* for (let i = 0; i < 7; i++) { %>
- [ ] Day <%= i + 1 %>: 
<%* } %>
```

### **3. JavaScript 실행**
```markdown
<%*
const today = tp.date.now("YYYY-MM-DD");
const weekStart = tp.date.weekstart("YYYY-MM-DD");
tR += `오늘: ${today}\n`;
tR += `이번 주 시작: ${weekStart}\n`;
%>
```

---

## 🎯 WJJ 활용 템플릿

### **1. 데일리 노트 템플릿**
```markdown
# 📅 <% tp.date.now("YYYY-MM-DD") %> 데일리 노트

> 요일: <% tp.date.now("dddd") %>

---

## ✅ 오늘의 체크리스트

### 점심 루틴
- [ ] 점심 먹기
- [ ] 칫솔 꺼내기
- [ ] 양말 신기

### 1시간 타이머 루틴
- [ ] 1시간 타이머 세팅
- [ ] 영단어 1일치

### 여유 시간 활용
- [ ] 유튜브 볼거 찾기
- [ ] 프로그래머스 0단계 1문제

### 운동 & 마무리
- [ ] 운동
- [ ] 샤워
- [ ] 게임 일퀘

---

## 📊 오늘 점수
- ✅ 완료: 0/10
- 🔥 연속: 0일

---

## 💬 오늘의 회고

### 잘한 점
- 

### 어려웠던 점
- 

### 내일 개선할 점
- 

---

## 📎 관련 노트
- [[📊 데일리 루틴 트래커]]
- [[영단어 매일 공부]]
- [[코테준비]]

---

**생성 시간**: <% tp.date.now("HH:mm") %>
```

### **2. 위클리 템플릿**
```markdown
# 📅 <% tp.date.now("YYYY") %>년 <% tp.date.now("MM") %>월 <% tp.date.now("W") %>주차

> 기간: <% tp.date.weekstart("YYYY-MM-DD") %> ~ <% tp.date.weekend("YYYY-MM-DD") %>

---

## 🎯 이번 주 목표

### 개발
- [ ] 
- [ ] 

### 취업 준비
- [ ] 
- [ ] 

### 자기계발
- [ ] 
- [ ] 

---

## 📅 요일별 계획

<%* const days = ["월", "화", "수", "목", "금", "토", "일"]; %>
<%* for (let i = 0; i < 7; i++) { %>

### <%= days[i] %>요일 (<% tp.date.weekday("YYYY-MM-DD", i) %>)
- [ ] 
- [ ] 

<%* } %>

---

## 📊 목표 달성률

- 개발: 0/2
- 취업 준비: 0/2
- 자기계발: 0/2

---

## 🏆 이번 주 보상
- 80% 이상: 게임 2시간
- 100%: 좋아하는 음식

---

## 📝 주간 회고

### 잘한 점
- 

### 어려웠던 점
- 

### 다음 주에 적용할 것
- 

---

**생성 시간**: <% tp.date.now("YYYY-MM-DD HH:mm") %>
```

### **3. 취업 준비 노트 템플릿**
```markdown
# 🎯 <% tp.file.title %>

**생성일**: <% tp.date.now("YYYY-MM-DD") %>
**마감일**: 
**진행률**: 0%

---

## 📋 개요

### 목표


### 범위


### 기대 결과


---

## ✅ 체크리스트

### 1단계
- [ ] 
- [ ] 

### 2단계
- [ ] 
- [ ] 

### 3단계
- [ ] 
- [ ] 

---

## 📅 타임라인

<%* const today = tp.date.now("YYYY-MM-DD"); %>

- [ ] 1단계: <% tp.date.now("YYYY-MM-DD", 7) %>
- [ ] 2단계: <% tp.date.now("YYYY-MM-DD", 14) %>
- [ ] 3단계: <% tp.date.now("YYYY-MM-DD", 21) %>

---

## 🚧 장애물


---

## 📝 회고


---

**상태**: 진행 중
**업데이트**: <% tp.date.now("YYYY-MM-DD") %>
```

---

## 🔧 폴더 템플릿

### **설정**
```
Settings → Templater → Folder Templates

Add New
- Folder: "일정/데일리"
- Template: "Templates/Daily Template.md"

Add New
- Folder: "일정/위클리"
- Template: "Templates/Weekly Template.md"
```

### **작동 방식**
1. 해당 폴더에 새 파일 생성
2. 자동으로 템플릿 적용
3. 변수 자동 치환

---

## 💡 실전 팁

### **1. Hotkeys 설정**
```
Settings → Hotkeys
- "Templater: Create new note from template"
  → Ctrl/Cmd + N
```

### **2. Startup Templates**
```javascript
// 옵시디언 시작 시 자동 실행
Settings → Templater → Startup Templates
→ "Templates/Startup.md"
```

### **3. System Commands**
```javascript
// 시스템 명령어 실행
Settings → Templater → System Commands
Enable: ON

<% tp.system.clipboard() %>
<% tp.system.paste() %>
```

---

## 🔗 관련 노트

- [[플러그인 추천 목록]]
- [[Dataview 가이드]] (DataviewJS 연동)
- [[QuickAdd 가이드]] (매크로 연동)

---

## ⚠️ 주의사항

1. **문법 오류**: `<%`와 `%>` 정확히 사용
2. **성능**: 복잡한 JS는 로딩 느려질 수 있음
3. **백업**: 템플릿 수정 전 백업 권장

---

## 📚 추가 리소스

### **공식 문서**
- GitHub: https://github.com/SilentVoid13/Templater
- 문서: https://silentvoid13.github.io/Templater/

### **예제**
- Templater Examples: 커뮤니티 예제 모음

---

**클로이 제작** 📋
**플러그인 버전**: 2.0+ (2026)
