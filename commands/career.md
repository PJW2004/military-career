---
description: 잡코리아/사람인에서 채용공고를 검색합니다
argument-hint: <회사명> [플랫폼]
allowed-tools: [mcp__job-search__search_jobs, mcp__job-search__search_jobs_bulk]
---

# 채용공고 검색

사용자가 채용공고를 검색하려고 합니다.

## 인자 파싱

사용자 입력: $ARGUMENTS

### 회사명 (필수)
- 사용자가 입력한 회사명을 **그대로** 전달하세요
- 임의로 줄이거나 변형하지 마세요
- 여러 회사를 쉼표로 구분한 경우 → `search_jobs_bulk` 사용

### 플랫폼 (선택)
- "잡코리아", "jobkorea" → platform: "jobkorea"
- "사람인", "saramin" → platform: "saramin"
- 미지정 시 → platform: "all" (양쪽 모두 검색)

## 실행

### 단일 회사
1. `search_jobs` 도구를 호출하세요
2. 결과를 아래 형식으로 정리하세요:
   - 공고 제목, 경력 조건, 학력, 지역, 마감일, URL
3. 공고가 없으면 회사명 변형(약어/정식명)을 시도해보라고 안내하세요

### 여러 회사 (쉼표 구분)
1. `search_jobs_bulk` 도구를 호출하세요
2. 요약 결과를 보여주세요
3. 상세 내용은 결과 파일 경로를 안내하세요

## 사용 예시

```
/career 삼성전자
/career 네이버, 카카오, 라인
/career LG에너지솔루션 잡코리아
```
