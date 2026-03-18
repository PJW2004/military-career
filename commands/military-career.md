---
description: 병역특례 지정업체 검색 후 해당 업체들의 채용공고까지 한 번에 조회합니다
argument-hint: <복무형태> [업종] [지역] [옵션]
allowed-tools: [mcp__military-service-workplace__search_military_companies, mcp__job-search__search_jobs, mcp__job-search__search_jobs_bulk]
---

# 병역특례 취업 파이프라인

사용자가 병역특례 지정업체를 검색하고, 해당 업체들의 실제 채용공고까지 한 번에 확인하려고 합니다.

## 인자 파싱

사용자 입력: $ARGUMENTS

`/military` 커맨드와 동일한 방식으로 파싱합니다:
- 복무형태 (필수): 산업기능요원/전문연구요원/승선근무예비역
- 업종, 지역, 기업규모, 현역/보충역 등 선택 옵션

## 실행 순서

### Step 1: 병역특례 지정업체 검색
1. `search_military_companies` 도구를 호출하세요
2. 결과에서 업체명 목록을 추출하세요
3. 사용자에게 검색된 업체 수와 목록을 먼저 보여주세요

### Step 2: 채용공고 일괄 검색
1. Step 1에서 얻은 업체명 목록으로 `search_jobs_bulk`를 호출하세요
2. 업체 수가 너무 많으면 (30개 초과):
   - 먼저 `is_hiring: true` 옵션으로 채용공고가 등록된 업체만 필터링
   - 또는 상위 30개만 검색하고 나머지는 추가 요청 시 검색
3. 진행 상황을 사용자에게 알려주세요

### Step 3: 결과 종합
1. 아래 형식으로 종합 결과를 정리하세요:

```
## 병역특례 취업 검색 결과

### 검색 조건
- 복무형태: {service_type}
- 업종: {industry} / 지역: {region}

### 요약
- 지정업체: {N}개
- 채용공고 있는 업체: {M}개
- 총 채용공고: {K}건

### 채용 중인 업체
| 회사명 | 공고 제목 | 경력 | 지역 | 마감일 | 링크 |
```

2. 채용공고가 없는 업체도 별도로 목록을 보여주세요 (직접 지원 가능성)
3. 결과가 많으면 상세 파일 경로를 안내하세요

## 사용 예시

```
/military-career 산업기능요원 정보처리 서울
/military-career 전문연구요원 경기도
/military-career 산기 게임SW 채용중
```
