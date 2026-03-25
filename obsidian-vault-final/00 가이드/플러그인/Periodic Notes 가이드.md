# Periodic Notes 플러그인 가이드

> 일일/주간/월간/분기/연간 노트 관리

**카테고리**: 노트 탐색 & 정리
**난이도**: 낮음
**추천도**: ⭐⭐⭐⭐

---

## 📋 개요

### **Periodic Notes란?**
일일 노트를 주간, 월간, 분기별, 연간 노트로 확장하고 각 주기별 전용 템플릿을 설정하는 플러그인

### **주요 기능**
- ✅ 일일 노트
- ✅ 주간 노트
- ✅ 월간 노트
- ✅ 분기별 노트
- ✅ 연간 노트
- ✅ 각 주기별 템플릿

---

## 🚀 설치 & 설정

### **1. 설치**
```
Settings → Community plugins → Browse
검색: "Periodic Notes"
Install → Enable
```

### **2. 기본 설정**
```
Settings → Periodic Notes
- Daily Notes: ON
- Weekly Notes: ON
- Monthly Notes: ON
- Quarterly Notes: OFF (선택)
- Yearly Notes: OFF (선택)
```

---

## 🎨 각 주기별 설정

### **1. 일일 노트**
```
Settings → Periodic Notes → Daily
- Folder: 일정/데일리
- Template: Templates/Daily Template.md
- Format: YYYY-MM-DD
```

### **2. 주간 노트**
```
Settings → Periodic Notes → Weekly
- Folder: 일정/위클리
- Template: Templates/Weekly Template.md
- Format: YYYY-[W]ww
```

### **3. 월간 노트**
```
Settings → Periodic Notes → Monthly
- Folder: 일정/먼슬리
- Template: Templates/Monthly Template.md
- Format: YYYY-MM
```

---

## ⚡ Calendar 연동

### **1. Calendar 플러그인 설치**
```
Calendar 플러그인 설치 필요
```

### **2. 연동 설정**
```
Settings → Calendar
- Weekly note: ON
- Monthly note: ON
```

### **3. 사용**
```
Calendar에서
- 날짜 클릭 → 일일 노트
- 주 번호 클릭 → 주간 노트
- 월 이름 클릭 → 월간 노트
```

---

## 🎯 WJJ 활용 예시

### **1. 데일리 → 위클리 연결**
```markdown
# 📅 2026-03-25 데일리 노트

## 이번 주 목표
![[2026-W13#목표]]

## 오늘의 진행
- [ ] 영단어
- [ ] 운동
- [ ] 프로그래머스

## 회고
...
```

### **2. 위클리 → 먼슬리 연결**
```markdown
# 📅 2026-W13 주간 노트

## 이번 달 목표
![[2026-03#목표]]

## 이번 주 목표
1. 
2. 
3. 

## 일일 요약
![[2026-03-23]]
![[2026-03-24]]
![[2026-03-25]]
```

### **3. 먼슬리 → 이번 달 회고**
```markdown
# 📅 2026-03 월간 노트

## 이번 달 목표
1. 
2. 
3. 

## 주간 요약
![[2026-W09]]
![[2026-W10]]
![[2026-W11]]
![[2026-W12]]
![[2026-W13]]

## 이번 달 회고

### 잘한 점
- 

### 개선할 점
- 

### 다음 달 목표
- 
```

---

## 💡 Templater 연동

### **1. 동적 날짜 생성**
```markdown
<% tp.date.now("YYYY-MM-DD") %> 데일리
<% tp.date.weekstart("YYYY-[W]ww") %> 주간
<% tp.date.now("YYYY-MM") %> 월간
```

### **2. 자동 링크 생성**
```markdown
## 이번 주
[[<% tp.date.weekstart("YYYY-[W]ww") %>]]

## 이번 달
[[<% tp.date.now("YYYY-MM") %>]]
```

---

## 🔗 관련 노트

- [[플러그인 추천 목록]]
- [[Calendar 가이드]]
- [[Templater 가이드]]

---

## ⚠️ 주의사항

1. **Calendar 플러그인**: 함께 사용 권장
2. **템플릿**: 각 주기별로 별도 템플릿 필요
3. **폴더 구조**: 주기별로 폴더 분리 권장

---

**클로이 제작** 📋
**플러그인 버전**: 1.0+ (2026)
