# Tasks 플러그인 가이드

> 옵시디언 내 강력한 작업 관리

**카테고리**: 생산성 & 자동화
**난이도**: 낮음
**추천도**: ⭐⭐⭐⭐

---

## 📋 개요

### **Tasks란?**
표준 마크다운 체크박스 위에 기한, 우선순위, 반복 기능을 추가하는 작업 관리 플러그인

### **주요 기능**
- ✅ 기한 설정
- ✅ 우선순위
- ✅ 반복 작업
- ✅ 필터링
- ✅ 정렬
- ✅ 그룹화

---

## 🚀 설치 & 설정

### **1. 설치**
```
Settings → Community plugins → Browse
검색: "Tasks"
Install → Enable
```

### **2. 기본 설정**
```
Settings → Tasks
- Global task filter: #task (선택)
- Set done date: ON
- Set recurrence date: ON
```

---

## 🎨 기본 문법

### **1. 기본 작업**
```markdown
- [ ] 일반 작업
```

### **2. 기한 설정**
```markdown
- [ ] 작업 📅 2026-03-26
```

### **3. 우선순위**
```markdown
- [ ] 높음 ⏫
- [ ] 중간 🔼
- [ ] 낮음 🔽
```

### **4. 반복 작업**
```markdown
- [ ] 매일 작업 🔁 every day
- [ ] 매주 작업 🔁 every week
- [ ] 매월 작업 🔁 every month
```

---

## ⚡ Tasks 쿼리

### **1. 모든 작업**
```tasks
not done
```

### **2. 기한 지난 작업**
```tasks
not done
due before today
```

### **3. 오늘 할일**
```tasks
not done
due today
```

### **4. 이번 주 작업**
```tasks
not done
due after today
due before in 7 days
```

### **5. 우선순위별**
```tasks
not done
sort by priority
```

### **6. 특정 태그**
```tasks
not done
tags include #취업
```

---

## 🎯 WJJ 활용 예시

### **1. 데일리 루틴 작업**
```markdown
# 오늘의 작업

## 습관
- [ ] 영단어 1시간 📅 2026-03-26 ⏫
- [ ] 운동 1시간 📅 2026-03-26 🔼
- [ ] 프로그래머스 1문제 📅 2026-03-26 🔽

## 취업 준비
- [ ] 이력서 수정 📅 2026-03-27 ⏫
- [ ] 포트폴리오 업데이트 📅 2026-03-28 🔼

---

## 진행 상황

```tasks
not done
path includes <% tp.file.folder() %>
```

## 완료된 작업

```tasks
done
path includes <% tp.file.folder() %>
```
```

### **2. 주간 작업 대시보드**
```markdown
# 📊 이번 주 작업 현황

## 마감 임박
```tasks
not done
due before in 3 days
sort by due
```

## 이번 주 전체
```tasks
not done
due after today
due before in 7 days
sort by due
```

## 완료율
```tasks
done
due after in 7 days
```
/ 
```tasks
not done
due after in 7 days
```
```

### **3. 취업 준비 추적**
```markdown
# 🎯 취업 준비 작업

## 진행 중
```tasks
not done
tags include #취업
sort by priority
sort by due
```

## 완료
```tasks
done
tags include #취업
```
```

---

## 💡 고급 기능

### **1. 그룹화**
```tasks
not done
group by priority
group by due
```

### **2. 제한**
```tasks
not done
limit 10
sort by due
```

### **3. 복잡한 필터**
```tasks
not done
(due before today) OR (priority is high)
sort by due
```

### **4. 완료 날짜 포함**
```tasks
done
short mode
```

---

## 🔄 반복 작업 패턴

### **매일**
```markdown
- [ ] 영단어 공부 🔁 every day 📅 2026-03-26
```

### **평일만**
```markdown
- [ ] 출근 준비 🔁 every weekday 📅 2026-03-26
```

### **특정 요일**
```markdown
- [ ] 주간 회고 🔁 every Friday 📅 2026-03-28
```

### **매월**
```markdown
- [ ] 월간 리포트 🔁 every month 📅 2026-04-01
```

---

## 📊 통계 쿼리

### **1. 완료율 계산**
```markdown
## 완료된 작업
```tasks
done
```

## 미완료 작업
```tasks
not done
```

## 완료율
<%*
const done = dv.pages().where(p => p.file.tasks).flatMap(p => p.file.tasks).where(t => t.completed).length;
const total = dv.pages().where(p => p.file.tasks).flatMap(p => p.file.tasks).length;
const percent = Math.round((done / total) * 100);
tR += `${percent}% (${done}/${total})`;
%>
```

### **2. 우선순위 분석**
```markdown
## 높은 우선순위
```tasks
not done
priority is high
```

## 중간 우선순위
```tasks
not done
priority is medium
```

## 낮은 우선순위
```tasks
not done
priority is low
```
```

---

## 🔧 Templater 연동

### **자동 작업 생성**
```markdown
<%* 
const today = tp.date.now("YYYY-MM-DD");
tR += `- [ ] 영단어 공부 📅 ${today} ⏫\n`;
tR += `- [ ] 운동 📅 ${today} 🔼\n`;
tR += `- [ ] 프로그래머스 📅 ${today} 🔽\n`;
%>
```

---

## 🔗 관련 노트

- [[플러그인 추천 목록]]
- [[Dataview 가이드]]
- [[Templater 가이드]]

---

## ⚠️ 주의사항

1. **문법**: 이모지 정확히 사용 (📅 ⏫ 🔼 🔽 🔁)
2. **쿼리**: 대용량 볼트에서는 느릴 수 있음
3. **동기화**: 모바일에서도 작동하지만 제한적

---

## 📚 추가 리소스

### **공식 문서**
- GitHub: https://github.com/obsidian-tasks-group/obsidian-tasks
- 문서: https://publish.obsidian.md/tasks/

### **예제**
- Tasks Examples: 커뮤니티 예제

---

**클로이 제작** 📋
**플러그인 버전**: 7.0+ (2026)
