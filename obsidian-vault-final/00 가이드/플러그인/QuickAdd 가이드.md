# QuickAdd 플러그인 가이드

> 빠른 콘텐츠 추가 & 매크로 자동화

**카테고리**: 생산성 & 자동화
**난이도**: 중간
**추천도**: ⭐⭐⭐⭐

---

## 📋 개요

### **QuickAdd란?**
매크로를 통해 볼트에 콘텐츠를 빠르게 추가하고 워크플로우를 자동화하는 플러그인

### **주요 기능**
- ✅ 빠른 노트 생성
- ✅ 템플릿 자동 적용
- ✅ 매크로 생성
- ✅ 다단계 워크플로우
- ✅ 선택지 제공

---

## 🚀 설치 & 설정

### **1. 설치**
```
Settings → Community plugins → Browse
검색: "QuickAdd"
Install → Enable
```

### **2. 기본 설정**
```
Settings → QuickAdd
- Manage Choices
```

---

## 🎨 기본 사용법

### **1. 선택(Choice) 만들기**
```
Settings → QuickAdd → Manage Choices

Add Choice
- Name: "습관 로그"
- Type: Template
```

### **2. 템플릿 설정**
```
Template Path: Templates/Habit Log.md
File Name Format: {{DATE:YYYY-MM-DD}}-habit
Create in folder: 일정/습관
```

### **3. 실행**
```
Command Palette → QuickAdd: 습관 로그
```

---

## ⚡ 매크로 만들기

### **1. 매크로 선택**
```
Settings → QuickAdd
- Add Choice → Macro
- Name: "데일리 루틴"
```

### **2. 단계 추가**
```
Configure Macro
1. Template: Daily Template
2. Capture: 오늘의 목표
3. Wait: 1초
4. Open: 방금 생성한 노트
```

### **3. 실행**
```
Command Palette → QuickAdd: 데일리 루틴
```

---

## 🎯 WJJ 활용 예시

### **1. 습관 로그 추가**
```
Name: 습관 로그
Type: Capture
Format:
---
date: {{DATE:YYYY-MM-DD}}
habit: 영단어
completed: false
---

## 오늘의 진행
- [ ] 1시간 타이머
- [ ] 영단어 1일치
```

### **2. 취업 준비 진행 추가**
```
Name: 취업 준비 진행
Type: Template
Template: Templates/Job Prep.md
Folder: 도전과제, 업적/취직/진행
```

### **3. 게임 개발 아이디어**
```
Name: 게임 아이디어
Type: Capture
Format:
# {{NAME}}

**생성일**: {{DATE:YYYY-MM-DD}}
**카테고리**: 

## 핵심 아이디어


## 참고 자료
- 
```

---

## 💡 고급 기능

### **1. 선택지 제공**
```markdown
Name: 작업 유형
Type: Capture
Choices:
- 개발
- 취업 준비
- 학습
```

### **2. 다단계 워크플로우**
```
Macro: 완벽한 데일리 시작
1. Template: Daily Template
2. Capture: 오늘의 목표
3. Capture: 감정 상태
4. Open: 오늘의 노트
5. Template: 습관 체크리스트
```

### **3. JavaScript 실행**
```javascript
// 매크로 내에서 JS 실행
const today = new Date();
const dayOfWeek = today.toLocaleDateString('ko-KR', { weekday: 'long' });
return `오늘은 ${dayOfWeek}입니다.`;
```

---

## 🔧 Templater 연동

### **1. Templater 변수 사용**
```
Template: Templates/Daily.md
Variables:
- {{DATE:YYYY-MM-DD}} → <% tp.date.now("YYYY-MM-DD") %>
- {{NAME}} → <% tp.file.title %>
```

### **2. 복합 매크로**
```
1. QuickAdd: 노트 생성
2. Templater: 템플릿 적용
3. QuickAdd: 추가 콘텐츠
```

---

## 🔗 관련 노트

- [[플러그인 추천 목록]]
- [[Templater 가이드]]
- [[Dataview 가이드]]

---

## ⚠️ 주의사항

1. **복잡성**: 매크로는 처음에 간단하게 시작
2. **테스트**: 새 매크로는 테스트 후 사용
3. **단축키**: 자주 쓰는 매크로는 단축키 설정

---

**클로이 제작** 📋
**플러그인 버전**: 1.0+ (2026)
