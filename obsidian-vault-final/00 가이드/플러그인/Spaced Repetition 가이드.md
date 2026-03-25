# Spaced Repetition 플러그인 가이드

> 간격 반복 학습으로 기억력 강화

**카테고리**: 학습 & 시각화
**난이도**: 중간
**추천도**: ⭐⭐⭐⭐

---

## 📋 개요

### **Spaced Repetition란?**
옵시디언 노트를 플래시카드로 전환하여 망각 곡선을 기반으로 최적의 간격으로 복습하게 도와주는 학습 플러그인

### **주요 기능**
- ✅ 플래시카드 생성
- ✅ 간격 반복 알고리즘
- ✅ 복습 스케줄링
- ✅ 통계 추적
- ✅ 데크 관리

---

## 🚀 설치 & 설정

### **1. 설치**
```
Settings → Community plugins → Browse
검색: "Spaced Repetition"
Install → Enable
```

### **2. 기본 설정**
```
Settings → Spaced Repetition
- Flashcard folders: "Flashcards"
- Review settings: 기본값
```

---

## 🎨 플래시카드 만들기

### **1. 기본 형식**
```markdown
#flashcard

Q: 질문 내용
?
A: 정답 내용
```

### **2. 카드 태그**
```markdown
#flashcard/english

Q: apple
?
A: 사과
```

### **3. 다중 라인**
```markdown
#flashcard

Q: 옵시디언의 핵심 기능은?
?
A: 
- 로컬 우선 저장
- 마크다운 기반
- 양방향 링크
- 그래프 뷰
```

---

## ⚡ 학습 방법

### **1. 복습 시작**
```
Command Palette → Spaced Repetition: Review flashcards
```

### **2. 평가 방법**
```
Again: 다시 보기 (1분 후)
Hard: 어려움 (10분 후)
Good: 보통 (1일 후)
Easy: 쉬움 (4일 후)
```

### **3. 단축키**
```
Space/Enter: Good
1: Again
2: Hard
3: Good
4: Easy
```

---

## 🎯 WJJ 활용 예시

### **1. 영단어 암기**
```markdown
#flashcard/english

Q: achieve
?
A: 달성하다, 성취하다

Q: consistent
?
A: 일관된, 지속적인

Q: significant
?
A: 중요한, 의미 있는
```

### **2. 개발 개념**
```markdown
#flashcard/programming

Q: REST API란?
?
A: Representational State Transfer
웹 서비스 아키텍처 스타일

Q: HTTP GET vs POST
?
A: 
GET: 데이터 조회
POST: 데이터 생성
```

### **3. 물리학 공식**
```markdown
#flashcard/physics

Q: 뉴턴 제2법칙
?
A: F = ma
힘 = 질량 × 가속도

Q: 운동량 보존 법칙
?
A: p1 + p2 = p1' + p2'
외력이 없을 때 운동량 합 일정
```

---

## 💡 고급 기능

### **1. 데크 만들기**
```markdown
#flashcard/english/vocabulary
```

### **2. 통계 확인**
```
Settings → Spaced Repetition → Statistics
```

### **3. 스케줄 확인**
```
Command Palette → Spaced Repetition: View scheduled
```

---

## 🔗 관련 노트

- [[플러그인 추천 목록]]
- [[영단어 매일 공부]]
- [[코테준비]]

---

## ⚠️ 주의사항

1. **매일 복습**: 효과를 위해 매일 10-15분 권장
2. **카드 분량**: 한 번에 너무 많이 만들지 않기
3. **복습 주기**: 초기에는 자주, 나중에는 간격 늘리기

---

**클로이 제작** 📋
**플러그인 버전**: 1.0+ (2026)
