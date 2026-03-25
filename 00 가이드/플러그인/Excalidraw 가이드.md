# Excalidraw 플러그인 가이드

> 시각적 사고를 위한 화이트보드 플러그인

**카테고리**: 시각화 & 학습
**난이도**: 중간
**추천도**: ⭐⭐⭐⭐⭐

---

## 📋 개요

### **Excalidraw란?**
옵시디언 내에서 직접 손그림 다이어그램, 마인드맵, UI 스케치를 만들 수 있는 가상 화이트보드

### **주요 기능**
- ✅ 손그림 다이어그램
- ✅ 마인드맵 빌더
- ✅ UI 스케치
- ✅ 순서도
- ✅ 개념도
- ✅ 노트 임베드

---

## 🚀 설치 & 설정

### **1. 설치**
```
Settings → Community plugins → Browse
검색: "Excalidraw"
Install → Enable
```

### **2. 기본 설정**
```
Settings → Excalidraw
- Default folder: "Excalidraw" (또는 원하는 폴더)
- Autosave: ON
- Template: 기본 템플릿 설정
```

---

## 🎨 핵심 기능

### **1. 드로잉 생성**
```bash
# 명령 팔레트
Ctrl/Cmd + P → "Excalidraw: Create new drawing"

# 리본 버튼
왼쪽 리본의 연필 아이콘 클릭
```

### **2. 마인드맵 빌더** (2026 NEW!)
```bash
# 마인드맵 시작
Excalidraw → MindMap Builder

# 단축키
ALT/OPT + V: 이미지/요소를 마인드맵 리프로 붙여넣기
ALT/OPT + E: 마크다운 링크 토글
```

### **3. 노트 연결**
```markdown
# 내부 링크
[[My file|Alias]]

# 트랜스클루전
![[myfile#^blockid]]

# 외부 링크
[Google](https://google.com)
```

### **4. 노트에 임베드**
```markdown
# 기본 임베드
![[diagram.excalidraw]]

# 크기 & 정렬
![[diagram.excalidraw|600x400|right-wrap]]
```

---

## ⚡ 고급 기능

### **1. ExcalidrawAutomate**

#### **스크립트 엔진**
```javascript
// 텍스트 주변에 박스 자동 추가
// 객체 간 화살표 자동 연결
// 동적 콘텐츠 생성
```

#### **Templater 연동**
```markdown
<%*
// 새 드로잉 생성
const drawing = await app.workspace.openPopoutLeaf("excalidraw");
await drawing.view.createDrawing();
%>
```

#### **DataviewJS 연동**
```dataviewjs
// 데이터 기반 다이어그램 생성
const pages = dv.pages("#task").where(t => t.completed);
// → SVG/PNG로 렌더링
```

---

### **2. 선형 캘린더 생성** (2026 트렌드)
```bash
# 스크립트 실행
Excalidraw → Scripts → Linear Calendar

# 커스터마이징
- 시작일/종료일 설정
- 색상 테마 적용
- 이벤트 마커 추가
```

---

### **3. Obsidian Publish 지원**
```
Settings → Excalidraw → Export
- Auto-export PNG/SVG: ON
- Dark/Light versions: ON
- Publish 호환: 자동 변환
```

---

## 🎯 WJJ 활용 예시

### **1. 게임 개발 설계**
```
게임 메커니즘 다이어그램
├─ 플레이어 시스템
├─ 전투 시스템
├─ 인벤토리 시스템
└─ UI 흐름도
```

### **2. 학습 노트 시각화**
```markdown
# 물리학 개념도

[역학] → [뉴턴 법칙]
         ↓
    [운동 방정식]
         ↓
    [응용 문제]
```

### **3. 취업 준비 로드맵**
```markdown
# 개발자 로드맵

[현재] → [기술 습득] → [포트폴리오] → [지원] → [면접]
```

---

## 💡 활용 팁

### **1. 템플릿 만들기**
```markdown
# .obsidian/templates/excalidraw-template.md

# 색상 팔레트 커스터마이징
Settings → Excalidraw → Template
→ Colors 수정
```

### **2. 단축키 활용**
```
R: 사각형
D: 다이아몬드
A: 화살표
T: 텍스트
L: 라인
E: 지우개
```

### **3. 레이어 관리**
```
Ctrl/Cmd + G: 그룹화
Ctrl/Cmd + Shift + G: 그룹 해제
Ctrl/Cmd + [: 뒤로 보내기
Ctrl/Cmd + ]: 앞으로 가져오기
```

---

## 🔗 관련 노트

- [[플러그인 추천 목록]]
- [[옵시디언 개선 제안]]
- [[로드맵]]

---

## 📚 추가 리소스

### **공식 문서**
- GitHub: https://github.com/zsviczian/obsidian-excalidraw-plugin
- 문서: https://zsviczian.github.io/obsidian-excalidraw-plugin/

### **튜토리얼**
- YouTube: "Visual PKM" by Zsolt Viczian
- Medium: Excalidraw 가이드

### **스크립트 라이브러리**
- Excalidraw Scripts: 커뮤니티 스크립트 모음

---

## ⚠️ 주의사항

1. **파일 크기**: 복잡한 드로잉은 파일이 커질 수 있음
2. **동기화**: Git 사용 시 .excalidraw 파일도 커밋 필요
3. **모바일**: 제한적 지원 (데스크탑 권장)

---

**클로이 제작** 📋
**플러그인 버전**: 2.0+ (2026)
