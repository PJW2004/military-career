# Marketplace 등록 가이드

이 문서는 `military-career` 플러그인을 Claude Code에서 사용하기 위한 마켓플레이스 등록 및 플러그인 설치 과정을 안내합니다.

## 사전 준비

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code)가 설치되어 있어야 합니다.
- 터미널(bash, zsh, PowerShell 등)에서 `claude` 명령어가 동작해야 합니다.

## 1단계: 마켓플레이스 등록

마켓플레이스를 등록하면 Claude Code가 이 저장소에서 플러그인을 검색할 수 있게 됩니다.

|명령어|인자|예시|
|--|--|--|
|marketplace add|소스(GitHub 경로, URL 등)|PJW2004/military-career|
|amrketplace update|마켓플레이스 이름|military-career-marketplace|

```bash
claude plugin marketplace add PJW2004/military-career
```
```bash
claude plugin marketplace update military-career-marketplace
```

### 확인

등록된 마켓플레이스 목록을 확인하려면:

```bash
claude plugin marketplace list
```

`military-career-marketplace`가 표시되면 정상적으로 등록된 것입니다.

## 2단계: 플러그인 설치

마켓플레이스가 등록되었으면 플러그인을 설치합니다.

### CLI에서 설치

```bash
claude plugin install military-career@military-career-marketplace
```

### Claude Code 대화 중 설치

```
/plugin install military-career@military-career-marketplace
```

### 설치 확인

설치된 플러그인 목록을 확인하려면:

```bash
claude plugin list
```

## 3단계: 사용

설치가 완료되면 아래 슬래시 커맨드를 사용할 수 있습니다:

| 커맨드 | 설명 |
|--------|------|
| `/military` | 병역특례 지정업체 검색 |
| `/career` | 잡코리아/사람인 채용공고 검색 |
| `/military-career` | 지정업체 검색 + 채용공고 통합 조회 |

사용 예시:

```
/military-career 산업기능요원 정보처리 서울
```

## 플러그인 업데이트

최신 버전으로 업데이트하려면:

```bash
claude plugin update military-career@military-career-marketplace
```

## 플러그인 제거

```bash
claude plugin uninstall military-career
```

마켓플레이스 등록도 함께 제거하려면:

```bash
claude plugin marketplace remove military-career-marketplace
```

## 문제 해결

### 마켓플레이스 등록이 안 되는 경우

- GitHub 저장소가 public인지 확인하세요.
- 저장소 루트에 `.claude-plugin/marketplace.json` 파일이 존재하는지 확인하세요.

### 플러그인 설치 후 커맨드가 동작하지 않는 경우

- Claude Code를 재시작해보세요.
- `claude plugin list`로 플러그인이 정상 설치되었는지 확인하세요.
- MCP 서버가 정상적으로 실행되는지 확인하세요:
  ```bash
  claude mcp list
  ```
