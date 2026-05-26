# MCP 서버 초보자 가이드

이 문서는 프롬프트 작업과 Codex 작업을 더 좋게 만들기 위해 먼저 연결하면 좋은 MCP 서버를 정리한다.

## MCP를 쉽게 말하면

MCP 서버는 AI에게 외부 도구를 붙여 주는 연결 장치다. AI가 GitHub를 보고, 내 프로젝트 폴더를 읽고, 브라우저 화면을 테스트하고, 최신 개발 문서를 찾아볼 수 있게 해준다.

## 먼저 추천하는 MCP 서버 4개

### 1. GitHub MCP Server

용도: GitHub 저장소, 이슈, PR, Actions, 코드 파일을 AI가 더 잘 읽고 다루게 한다.

추천 이유:
- prompts.chat 같은 프롬프트 저장소 관리에 가장 중요하다.
- Codex가 저장소 상태를 추측하지 않고 파일과 PR을 직접 확인하는 데 도움이 된다.
- 브랜치, 커밋, 변경 파일을 확인하기 좋다.

공식 저장소:

```text
https://github.com/github/github-mcp-server
```

원격 MCP URL:

```text
https://api.githubcopilot.com/mcp/
```

### 2. Filesystem MCP Server

용도: AI가 내 컴퓨터의 허용된 폴더만 읽고 쓰게 한다.

추천 이유:
- 로컬에 있는 프롬프트 파일을 정리할 수 있다.
- GitHub에 올리기 전에 폴더 안 파일을 점검할 수 있다.
- 전체 컴퓨터가 아니라 프로젝트 폴더 하나만 열 수 있어 안전하다.

공식 저장소:

```text
https://github.com/modelcontextprotocol/servers/tree/main/src/filesystem
```

초보자 보안 원칙:

```text
전체 홈 폴더를 열지 말고 ~/work/prompts.chat 같은 프로젝트 폴더 하나만 허용한다.
```

### 3. Playwright MCP Server

용도: AI가 브라우저 화면을 열고 웹 UI를 확인하게 한다.

추천 이유:
- 웹사이트, 프롬프트 UI, 로그인 화면, 오류 화면을 직접 확인할 수 있다.
- 스크린샷만 보고 추측하는 것보다 정확하다.
- WeKnora나 prompts.chat 관련 웹 화면을 테스트하기 좋다.

공식 저장소:

```text
https://github.com/microsoft/playwright-mcp
```

### 4. Context7 MCP

용도: AI가 최신 라이브러리 문서와 코드 예시를 찾아보게 한다.

추천 이유:
- 오래된 지식으로 틀린 코드를 만드는 일을 줄인다.
- Next.js, Supabase, Docker, Playwright 같은 최신 설정을 확인하기 좋다.
- 프롬프트에 `use context7`라고 적으면 관련 문서를 가져오게 할 수 있다.

공식 저장소:

```text
https://github.com/upstash/context7
```

원격 MCP URL:

```text
https://mcp.context7.com/mcp
```

## Mac에서 기본 준비

Mac에서는 Homebrew가 있으면 설치가 쉽다.

```bash
brew install node git gh
npm --version
gh auth login
```

Homebrew가 없다면 먼저 설치해야 한다.

```text
https://brew.sh/
```

## VS Code에서 연결하는 기본 생각

VS Code는 MCP 설정 파일에 서버를 적는다. 초보자는 먼저 GitHub MCP와 Playwright MCP부터 연결하는 것이 좋다.

예시:

```json
{
  "servers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/"
    },
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

## Cursor에서 연결하는 기본 생각

Cursor는 Settings에서 MCP를 열고 서버를 추가한다.

Playwright 예시:

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

Filesystem 예시:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/Users/YOUR_NAME/work/prompts.chat"
      ]
    }
  }
}
```

## Codex CLI에서 연결하는 기본 생각

Codex CLI를 쓴다면 MCP 서버를 추가하거나 설정 파일을 편집한다.

Playwright 예시:

```bash
codex mcp add playwright npx "@playwright/mcp@latest"
```

설정 파일 방식 예시:

```toml
[mcp_servers.playwright]
command = "npx"
args = ["@playwright/mcp@latest"]
```

## 추천 연결 순서

1. GitHub MCP
2. Filesystem MCP
3. Playwright MCP
4. Context7 MCP

## 주의사항

- 인증값은 GitHub에 커밋하지 않는다.
- Filesystem MCP는 허용 폴더를 꼭 제한한다.
- 처음에는 읽기 위주로 연결하고, 쓰기 권한은 필요할 때만 준다.
- 잘 모르는 MCP 서버는 바로 설치하지 말고 공식 저장소와 문서를 확인한다.
