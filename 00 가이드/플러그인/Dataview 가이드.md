# Dataview 플러그인 가이드

> 노트를 데이터베이스처럼 쿼리하기

**카테고리**: 생산성 & 자동화
**난이도**: 높음
**추천도**: ⭐⭐⭐⭐⭐

---

## 📋 개요

### **Dataview란?**
옵시디언 노트를 SQL처럼 쿼리하여 대시보드, 색인, 동적 목록을 만드는 플러그인

### **주요 기능**
- ✅ 데이터베이스 쿼리
- ✅ 대시보드 생성
- ✅ 자동 인덱스
- ✅ 태그 필터링
- ✅ 날짜 기반 쿼리
- ✅ 테이블, 리스트, 뷰

---

## 🚀 설치 & 설정

### **1. 설치**
```
Settings → Community plugins → Browse
검색: "Dataview"
Install → Enable
```

### **2. 기본 설정**
```
Settings → Dataview
- Enable JavaScript Queries: ON
- Enable Inline Queries: ON
- Automatic View Refreshing: ON
```

---

## 🎨 기본 문법

### **1. 리스트 (LIST)**
```dataview
LIST
FROM "습관-인간개조 프로젝트"
WHERE contains(tags, "습관")
```

### **2. 테이블 (TABLE)**
```dataview
TABLE
  file.ctime as "생성일",
  tags as "태그"
FROM "도전과제, 업적"
WHERE file.name != "도전과제, 업적"
```

### **3. 작업 (TASK)**
```dataview
TASK
FROM "일정/데일리"
WHERE !completed
```

---

## ⚡ 고급 쿼리

### **1. 날짜 필터링**
```dataview
TABLE
  file.name as "파일명",
  file.mtime as "수정일"
FROM ""
WHERE file.mtime >= date(today) - dur(7 days)
SORT file.mtime DESC
```

### **2. 태그 기반**
```dataview
LIST
FROM #취업
WHERE contains(file.name, "이력서")
```

### **3. 메타데이터 활용**
```markdown
---
progress: 50
priority: high
due: 2026-04-30
---
```

```dataview
TABLE
  progress as "진행률",
  priority as "우선순위",
  due as "마감일"
FROM ""
WHERE due <= date(today) + dur(30 days)
SORT due ASC
```

---

## 🎯 WJJ 활용 예시

### **1. 습관 진행 대시보드**
```dataview
TABLE
  choice(영단어, "✅", "❌") as "영단어",
  choice(운동, "✅", "❌") as "운동",
  choice(프로그래머스, "✅", "❌") as "코테"
FROM "일정/데일리"
WHERE file.name != "2026-03-25"
SORT file.name DESC
LIMIT 7
```

### **2. 취업 준비 진행 추적**
```dataview
TABLE
  progress as "진행률 %",
  choice(progress >= 80, "🔥", 
         choice(progress >= 50, "⏳", "❗")) as "상태"
FROM "도전과제, 업적/취직"
WHERE progress != null
SORT progress DESC
```

### **3. 최근 학습 노트**
```dataview
LIST
FROM "공부"
WHERE file.mtime >= date(today) - dur(7 days)
SORT file.mtime DESC
LIMIT 10
```

---

## 💡 DataviewJS (JavaScript 쿼리)

### **1. 고급 통계**
```dataviewjs
const pages = dv.pages("#task")
  .where(t => t.completed);
  
dv.paragraph(`완료된 작업: ${pages.length}개`);
```

### **2. 차트 생성**
```dataviewjs
const data = dv.pages()
  .groupBy(p => p.file.folder)
  .map(g => ({ folder: g.key, count: g.rows.length }));
  
dv.table(["폴더", "파일 수"], 
  data.map(d => [d.folder, d.count]));
```

### **3. 조건부 포맷팅**
```dataviewjs
dv.el("div", `
  <div style="background: linear-gradient(to right, #4CAF50 ${progress}%, transparent ${progress}%);">
    진행률: ${progress}%
  </div>
`);
```

---

## 🔧 실전 템플릿

### **데일리 노트 대시보드**
```markdown
# 📊 오늘의 진행 상황

## 완료된 작업
```dataview
TASK
FROM "일정/데일리/<% tp.date.now('YYYY-MM-DD') %>.md"
WHERE completed
```

## 미완료 작업
```dataview
TASK
FROM "일정/데일리/<% tp.date.now('YYYY-MM-DD') %>.md"
WHERE !completed
```
```

### **주간 리뷰**
```markdown
# 📅 이번 주 활동

```dataview
TABLE
  length(file.tasks.completed) as "완료",
  length(file.tasks) as "전체"
FROM "일정/데일리"
WHERE file.name >= "<% tp.date.weekstart('YYYY-MM-DD') %>"
  AND file.name <= "<% tp.date.weekend('YYYY-MM-DD') %>"
```
```

---

## 📚 함수 레퍼런스

### **날짜 함수**
```
date(today) - 오늘
date(yesterday) - 어제
date(tomorrow) - 내일
dur(7 days) - 7일 기간
```

### **문자열 함수**
```
contains(text, "keyword") - 포함 여부
startswith(text, "prefix") - 시작 문자
endswith(text, "suffix") - 끝 문자
length(text) - 길이
```

### **수학 함수**
```
sum(list) - 합계
average(list) - 평균
min(list) / max(list) - 최소/최대
```

---

## 🔗 관련 노트

- [[플러그인 추천 목록]]
- [[Templater 가이드]] (DataviewJS 연동)
- [[📊 데일리 루틴 트래커]]

---

## ⚠️ 주의사항

1. **성능**: 대량 쿼리는 로딩 시간 증가
2. **캐시**: 변경사항 반영까지 시간 걸릴 수 있음
3. **복잡성**: 초보자는 LIST/TABLE부터 시작

---

## 📚 추가 리소스

### **공식 문서**
- GitHub: https://github.com/michaelrenaissance/dataview
- 문서: https://blacksmithgu.github.io/obsidian-dataview/

### **예제**
- Dataview Example Vault: 예제 모음
- Reddit: r/ObsidianMD

---

**클로이 제작** 📋
**플러그인 버전**: 1.0+ (2026)
