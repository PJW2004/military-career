---
description: 병역특례(산업기능요원/전문연구요원/승선근무예비역) 지정업체를 검색합니다
argument-hint: <복무형태> [업종] [지역] [옵션]
allowed-tools: [mcp__military-service-workplace__search_military_companies]
---

# 병역특례 지정업체 검색

사용자가 병역특례 지정업체를 검색하려고 합니다.

## 인자 파싱

사용자 입력: $ARGUMENTS

아래 규칙에 따라 인자를 파싱하세요:

### 복무형태 (필수)
- "산업기능요원", "산기", "산업" → service_type: "산업기능요원"
- "전문연구요원", "전문연구", "연구" → service_type: "전문연구요원"
- "승선근무예비역", "승선" → service_type: "승선근무예비역"
- 미지정 시 → 사용자에게 물어보세요

### 선택 옵션 (자연어에서 추출)
- 업종 키워드: "정보처리", "전자", "게임SW", "기계" 등 → industry_sectors
- 지역 키워드: "서울", "경기", "부산" 등 → city_province (정식 명칭으로 변환: "서울" → "서울특별시")
- 기업규모: "대기업", "중소기업", "중견기업" → company_size
- 회사명 언급 → company_name
- "채용중", "채용 중", "공고 있는" → is_hiring: true
- "현역", "보충역" → military_service_type

## 실행

1. `search_military_companies` 도구를 호출하세요
2. 결과를 깔끔한 표 형식으로 정리하세요
3. 총 업체 수를 안내하세요
4. 채용공고가 궁금하면 `/career <회사명>`으로 이어서 검색할 수 있다고 안내하세요

## 사용 예시

```
/military 산업기능요원 정보처리 서울
/military 전문연구요원 경기도 채용중
/military 산기 전자 대기업
/military 승선
```
