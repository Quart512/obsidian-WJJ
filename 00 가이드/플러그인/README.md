# 📦 옵시디언 플러그인 완벽 가이드

> WJJ를 위한 맞춤형 플러그인 추천 및 설정 가이드

**작성일**: 2026-03-22
**업데이트**: 2026-03-25

---

## 🎯 플러그인이란?

옵시디언의 기본 기능을 확장하는 추가 도구입니다. **코어 플러그인**은 옵시디언이 기본 제공하고, **커뮤니티 플러그인**은 개발자들이 만들어 공유하는 플러그인입니다.

---

## 🚀 설치 방법

### 1단계: 커뮤니티 플러그인 활성화
1. `Ctrl/Cmd + ,` 로 **설정** 열기
2. 왼쪽 메뉴에서 **커뮤니티 플러그인** 클릭
3. **제한 모드 끄기** 버튼 클릭 (보안 경고 확인)

### 2단계: 플러그인 설치
1. **커뮤니티 플러그인 탐색** 버튼 클릭
2. 검색창에 플러그인 이름 입력
3. **설치** 클릭
4. 설치 후 **활성화** 클릭

> [!warning] 플러그인 보안
> 커뮤니티 플러그인은 옵시디언 팀이 아닌 개발자들이 만든 것입니다. 별점이 높고 다운로드 수가 많은 검증된 플러그인을 설치하는 것을 권장합니다.

---

## 🏆 핵심 추천 플러그인 TOP 8

### 1. **Dataview** ⭐⭐⭐⭐⭐

**용도**: 노트를 데이터베이스처럼 쿼리하고 표/목록으로 표시

옵시디언 플러그인 중 가장 강력한 플러그인 중 하나입니다. 프론트매터 데이터와 태그를 기반으로 노트를 동적으로 조회합니다.

**설치명**: `Dataview`

**기본 사용 예시**

태그가 `#독서` 인 모든 노트를 최신순으로 표시:
````markdown
```dataview
TABLE title, author, rating
FROM #독서
SORT file.mtime DESC
```
````

진행 중인 프로젝트 목록:
````markdown
```dataview
LIST
FROM "01 프로젝트"
WHERE status = "진행중"
SORT file.name ASC
```
````

이번 주 생성된 노트:
````markdown
```dataview
TABLE file.ctime AS "생성일"
FROM ""
WHERE file.ctime >= date(today) - dur(7 days)
SORT file.ctime DESC
```
````

**WJJ 활용**: [[Dataview 가이드|상세 가이드 보기]]

---

### 2. **Templater** ⭐⭐⭐⭐⭐

**용도**: 변수, 날짜, JavaScript 로직이 포함된 고급 템플릿

기본 코어 플러그인인 '템플릿'보다 훨씬 강력합니다. 현재 날짜, 파일명, 사용자 입력 등을 동적으로 삽입할 수 있습니다.

**설치명**: `Templater`

**기본 변수들**
```markdown
<% tp.date.now("YYYY-MM-DD") %>          현재 날짜
<% tp.date.now("HH:mm") %>               현재 시간
<% tp.file.title %>                       현재 파일명
<% tp.date.now("dddd", 0, "ko") %>       요일 (한국어)
<% await tp.system.prompt("제목?") %>    사용자 입력 받기
```

**일일 노트 템플릿 예시**
```markdown
---
date: <% tp.date.now("YYYY-MM-DD") %>
day: <% tp.date.now("dddd") %>
tags:
  - 일일노트
---

# <% tp.date.now("YYYY년 MM월 DD일 (ddd)") %>

## 오늘의 목표
- [ ]

## 오늘 한 일

## 배운 것

## 내일 할 일
- [ ]
```

**WJJ 활용**: [[Templater 가이드|상세 가이드 보기]]

---

### 3. **Excalidraw** ⭐⭐⭐⭐⭐

**용도**: 노트 안에 손글씨 스타일의 다이어그램과 스케치 삽입

아이디어를 시각적으로 표현하거나, 마인드맵, 플로우차트 등을 그릴 수 있습니다.

**설치명**: `Excalidraw`

**사용 방법**
1. `Ctrl/Cmd + P` → `Excalidraw: Create new drawing` 실행
2. 캔버스에서 그림 그리기
3. 다른 노트에서 `![[그림파일.excalidraw]]` 로 임베드

**활용 예시**
- 프로젝트 구조 시각화
- 알고리즘 흐름도
- 아이디어 브레인스토밍 맵
- 개념 간의 관계도

**WJJ 활용**: [[Excalidraw 가이드|상세 가이드 보기]]

---

### 4. **Tasks** ⭐⭐⭐⭐⭐

**용도**: 볼트 전체에서 할일을 수집하고 필터링

어떤 노트에 있든 `- [ ]` 형식의 할일을 모아서 보여줍니다. 마감일, 반복, 우선순위 설정도 가능합니다.

**설치명**: `Obsidian Tasks`

**할일 작성 형식**
```markdown
- [ ] 보고서 작성 📅 2026-03-25 ⏫
- [ ] 이메일 답장 📅 2026-03-22 🔁 every day
- [x] 회의 참석 ✅ 2026-03-21
```

**날짜 아이콘 의미**
- `📅` : 마감일 (due date)
- `⏫` : 높은 우선순위
- `🔼` : 보통 우선순위
- `🔁` : 반복 설정

**Tasks 쿼리 예시**

오늘 마감인 할일 표시:
````markdown
```tasks
due today
not done
```
````

**WJJ 활용**: [[Tasks 가이드|상세 가이드 보기]]

---

### 5. **Calendar** ⭐⭐⭐⭐

**용도**: 캘린더 형식으로 일일/주간 노트 탐색 및 생성

오른쪽 사이드바에 작은 캘린더가 표시되며, 날짜를 클릭하면 해당 날의 일일 노트로 이동하거나 생성할 수 있습니다.

**설치명**: `Calendar`

**함께 설치 권장**: `Periodic Notes` 플러그인과 함께 사용하면 주간, 월간 노트도 관리할 수 있습니다.

**WJJ 활용**: [[Calendar 가이드|상세 가이드 보기]]

---

### 6. **QuickAdd** ⭐⭐⭐⭐

**용도**: 빠른 노트 추가, 자동화 워크플로우, 매크로 구성

새 노트를 빠르게 추가하거나, 반복 작업을 자동화하는 데 사용합니다.

**설치명**: `QuickAdd`

**주요 기능**
1. **Capture** : 빠른 텍스트 입력을 특정 노트에 추가
2. **Template** : 템플릿을 적용한 새 노트 즉시 생성
3. **Macro** : 여러 QuickAdd 명령을 묶어서 실행

**WJJ 활용**: [[QuickAdd 가이드|상세 가이드 보기]]

---

### 7. **Advanced Tables** ⭐⭐⭐

**용도**: 마크다운 표를 쉽고 빠르게 만들고 편집

기본 마크다운 표는 작성하기 불편합니다. 이 플러그인을 설치하면 `Tab` 으로 셀 이동, `Enter` 로 새 행 추가, 자동 열 정렬이 지원됩니다.

**설치명**: `Advanced Tables`

**사용 방법**
- `|` 를 입력하고 표 작성 시작
- `Tab` : 다음 셀로 이동
- `Shift + Tab` : 이전 셀로 이동
- `Enter` : 새 행 추가

**WJJ 활용**: [[Advanced Tables 가이드|상세 가이드 보기]]

---

### 8. **Obsidian Git** ⭐⭐⭐⭐

**용도**: 볼트를 Git으로 자동 백업하고 버전 관리

옵시디언 Sync를 구독하지 않아도 GitHub 등을 통해 무료로 볼트를 백업하고 기기 간 동기화할 수 있습니다.

**설치명**: `Obsidian Git`

**주요 설정**
- Auto backup interval: 자동 커밋 간격 (분 단위, 예: 10분마다)
- Auto push on backup: 자동 커밋 시 원격 저장소에도 푸시

---

## 📚 추가 추천 플러그인

### **학습 & 시각화**

#### **Spaced Repetition** ⭐⭐⭐⭐
**용도**: 옵시디언 노트를 플래시카드로 전환하여 간격 반복 학습

**WJJ 활용**: 영단어 암기, 개념 학습
**상세 가이드**: [[Spaced Repetition 가이드]]

#### **HoverNotes** ⭐⭐⭐
**용도**: 비디오 콘텐츠에서 타임스탬프가 찍힌 노트와 스크린샷 캡처

**WJJ 활용**: 개발 강의 학습
**상세 가이드**: [[HoverNotes 가이드]]

---

### **노트 탐색 & 정리**

#### **Periodic Notes** ⭐⭐⭐⭐
**용도**: 일일 노트를 주간, 월간, 분기별, 연간 노트로 확장

**상세 가이드**: [[Periodic Notes 가이드]]

#### **Omnisearch** ⭐⭐⭐
**용도**: 전체 텍스트 검색 강화

**상세 가이드**: [[Omnisearch 가이드]]

#### **Recent Files** ⭐⭐⭐
**용도**: 최근 열어본 파일 목록 표시

**상세 가이드**: [[Recent Files 가이드]]

---

### **유틸리티 & UI 개선**

#### **Commander** ⭐⭐⭐
**용도**: 옵시디언 UI에 커스텀 버튼 추가

**상세 가이드**: [[Commander 가이드]]

#### **Custom Frames** ⭐⭐⭐
**용도**: 웹페이지를 옵시디언 내에 임베드

**상세 가이드**: [[Custom Frames 가이드]]

#### **Make.md** ⭐⭐⭐
**용도**: 직관적인 편집 기능, Spaces, Contexts

**상세 가이드**: [[Make.md 가이드]]

---

## 🎯 WJJ 추천 플러그인 조합

### **취업 준비용** 📋
```
✅ Dataview - 진행 상황 추적
✅ Tasks - 할일 관리
✅ Calendar - 일정 관리
✅ Templater - 템플릿 자동화
✅ Excalidraw - 학습 다이어그램
```

### **습관 관리용** 🔄
```
✅ Periodic Notes - 정기 리뷰
✅ QuickAdd - 빠른 로그 추가
✅ Spaced Repetition - 영단어 암기
✅ Dataview - 습관 대시보드
```

### **게임 개발용** 🎮
```
✅ Excalidraw - 게임 설계
✅ HoverNotes - 강의 학습
✅ Dataview - 진행 추적
✅ QuickAdd - 아이디어 노트
```

---

## 🔧 설치 우선순위

### **1단계 (오늘)**
1. Templater
2. Dataview
3. Calendar
4. Tasks

### **2단계 (이번 주)**
5. Excalidraw
6. QuickAdd
7. Periodic Notes

### **3단계 (필요시)**
8. Omnisearch
9. Spaced Repetition
10. Advanced Tables

---

## 📚 코어 플러그인 확인사항

옵시디언 기본 제공 플러그인 중 반드시 활성화하면 좋은 것들:

- **Daily notes** : 일일 노트 기능
- **Templates** : 기본 템플릿 기능
- **Backlinks** : 백링크 패널
- **Outgoing links** : 아웃고잉 링크 패널
- **Tag pane** : 태그 목록 패널
- **File recovery** : 노트 자동 백업
- **Workspaces** : 여러 작업 공간 저장/전환
- **Outline** : 현재 노트의 헤딩 목차

**설정 > 코어 플러그인** 에서 활성화할 수 있습니다.

---

## 🔗 관련 가이드

### **개별 플러그인 가이드**
- [[Excalidraw 가이드]]
- [[Dataview 가이드]]
- [[Tasks 가이드]]
- [[Templater 가이드]]
- [[Calendar 가이드]]
- [[QuickAdd 가이드]]
- [[Periodic Notes 가이드]]
- [[Omnisearch 가이드]]
- [[Spaced Repetition 가이드]]
- [[HoverNotes 가이드]]
- [[Advanced Tables 가이드]]
- [[Custom Frames 가이드]]
- [[Commander 가이드]]
- [[Make.md 가이드]]
- [[Recent Files 가이드]]

### **기본 가이드**
- [[옵시디언 시작하기]]
- [[마크다운 작성법]]
- [[템플릿 모음]]
- [[메모 관리 시스템]]
- [[학습에 옵시디언 활용하기]]

---

## 📚 추가 리소스

### **공식 문서**
- Obsidian Hub: https://publish.obsidian.md/hub/
- Plugin Directory: https://obsidian.md/plugins

### **커뮤니티**
- Discord: https://discord.com/invite/obsidianmd
- Reddit: r/ObsidianMD
- Forum: https://forum.obsidian.md

### **튜토리얼**
- YouTube: "Obsidian Office Hours"
- 블로그: https://obsidian.rocks

---

## ⚠️ 주의사항

### **플러그인 관리**
1. **필요한 것만 설치** (2,500개 중 골라서)
2. **정기적 정리** (사용 안 하는 플러그인 삭제)
3. **업데이트 확인** (보안 & 버그 수정)

### **호환성**
- 일부 플러그인은 모바일 미지원
- 충돌 가능성 있음
- 백업 필수

---

**클로이 제작** 📋
**작성일**: 2026-03-22
**업데이트**: 2026-03-25
