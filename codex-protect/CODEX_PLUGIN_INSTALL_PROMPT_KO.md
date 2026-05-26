# Codex 스킬·플러그인 실제 적용 프롬프트

아래 프롬프트를 Codex 작업에 그대로 붙여넣는다.

```text
저장소:
tnsqhr0108-dev/math-masterbook

브랜치:
Main

연결 저장소:
- tnsqhr0108-dev/WeKnora main
- tnsqhr0108-dev/prompts.chat main
- tnsqhr0108-dev/system_prompts_leaks main

작업명:
스킬, 플러그인, MCP, 앱 연결 실제 적용 상태 점검 및 작동 가능한 구성 만들기

목표:
아직 설치/적용되지 않은 스킬, 플러그인, MCP, 앱 연결을 전부 점검하고, Codex가 실제로 사용할 수 있는 것은 설정 파일/문서/테스트/체크리스트로 적용해줘. 사용자가 직접 OAuth 승인해야 하는 앱은 직접 설치 완료라고 말하지 말고, 사용자 단계와 검증 방법을 만들어줘.

반드시 먼저 읽을 파일:
1. codex-protect/README_KO.md
2. codex-protect/LOAD_ORDER.md
3. codex-protect/ANSWER_PLAYBOOK_KO.md
4. AGENTS.md
5. docs/CODEX_ANSWER_QUALITY_POLICY.md
6. docs/CODEX_1000PLUS_FEATURE_LOADER_KO.md
7. docs/FEATURE_REGISTER_1000PLUS_KO.md
8. scripts/generate_feature_register_1000plus.py

반드시 먼저 실행:
```bash
pwd
git rev-parse --show-toplevel
git remote -v
git symbolic-ref --short HEAD 2>/dev/null || true
git branch --show-current 2>/dev/null || true
git rev-parse HEAD
git status --short
find . -maxdepth 3 -type f | sort
python3 scripts/generate_feature_register_1000plus.py --check || true
```

중요 원칙:
- 실제로 연결/설치/검증하지 못한 것은 완료라고 말하지 마.
- ChatGPT 앱 연결, OAuth 승인, Canva, Google Drive, Acrobat, Notion, Airtable 같은 외부 앱은 사용자가 직접 승인해야 하므로 `사용자 승인 대기`로 표시해.
- Codex가 직접 할 수 있는 일은 저장소 파일, 설정, 스크립트, 문서, 점검표, GitHub Actions, MCP 설정 예시, 테스트 명령 작성이다.
- API 키, 토큰, 쿠키, 비밀번호를 출력하거나 커밋하지 마.
- Android Debian 사용자를 기준으로 복사/붙여넣기 가능한 명령을 만들어줘.

점검할 공개 앱/플러그인/MCP 후보:
1. GitHub MCP
2. Context7 MCP
3. Google Drive
4. OneDrive
5. Dropbox
6. Canva
7. Figma
8. Adobe Express
9. Adobe Acrobat
10. Notion
11. Airtable
12. Google Sheets
13. Google Docs
14. Microsoft Excel
15. Microsoft Word
16. Slack
17. Linear
18. Jira
19. Trello
20. Asana
21. Playwright MCP
22. Filesystem MCP
23. WeKnora MCP
24. Postgres MCP
25. SQLite MCP
26. Browser/Search
27. Python/Notebook
28. PDF tool
29. Spreadsheet tool
30. Image generation/design tool

각 후보마다 아래 상태 중 하나를 붙여:
- 연결 완료
- 설치 가능
- 사용자 승인 대기
- Mac/PC 필요
- 서버 필요
- Android Debian에서 가능
- 보류
- 제외
- 검수하지 못함

반드시 만들거나 업데이트할 파일:
- codex-protect/PLUGIN_AND_SKILL_STATUS_KO.md
- codex-protect/PLUGIN_INSTALL_RUNBOOK_KO.md
- codex-protect/MCP_CLIENT_CONFIG_EXAMPLES_KO.md
- codex-protect/USER_OAUTH_TODO_KO.md
- codex-protect/SKILL_APPLY_CHECKLIST_KO.md
- outputs/plugin_skill_status_report.md
- outputs/plugin_skill_status_report.json

파일별 내용:

1. codex-protect/PLUGIN_AND_SKILL_STATUS_KO.md
- 전체 앱/MCP/스킬 후보 표
- 상태
- 실제 적용 가능 여부
- 필요한 사용자 행동
- Codex가 할 수 있는 행동
- 검증 명령

2. codex-protect/PLUGIN_INSTALL_RUNBOOK_KO.md
- 초보자용 설치/연결 순서
- ChatGPT 앱에서 연결해야 하는 항목
- Android Debian에서 가능한 항목
- Mac/PC가 있어야 가능한 항목
- WeKnora 서버가 있어야 가능한 항목

3. codex-protect/MCP_CLIENT_CONFIG_EXAMPLES_KO.md
- GitHub MCP
- Context7 MCP
- Playwright MCP
- Filesystem MCP
- WeKnora MCP
- Postgres MCP
- SQLite MCP
설정 예시를 작성해.
단, 토큰/키는 예시 placeholder만 사용해.

4. codex-protect/USER_OAUTH_TODO_KO.md
- 사용자가 직접 ChatGPT 앱에서 승인해야 하는 목록
- Google Drive, Canva, Figma, Acrobat, Notion, Airtable 등 연결 방법
- 연결 후 테스트 문장

5. codex-protect/SKILL_APPLY_CHECKLIST_KO.md
- 답변에 항상 적용할 내부 스킬 30개 이상
- PDF/RAG/GAN/하니스/다중 에이전트/오케스트레이션/감점표별 조건부 스킬
- 실제 완료 기준

6. outputs/plugin_skill_status_report.md/json
- 현재 점검 결과
- 설치 완료/대기/검수하지 못함/제외 목록
- 남은 작업

검증해야 할 것:
- GitHub MCP는 실제로 저장소 조회가 되는지 확인.
- Context7은 연결되어 있지 않으면 사용자 승인 대기로 표시.
- Google Drive/Canva/Figma/Acrobat/Notion/Airtable은 ChatGPT 앱 연결이 필요하므로 사용자 승인 대기로 표시.
- Playwright MCP와 Filesystem MCP는 Codex 모바일에서 직접 사용하기 어렵고 Mac/PC가 필요하다고 표시.
- WeKnora MCP는 WeKnora 서버 실행 전에는 대기로 표시.
- Postgres/SQLite MCP는 실제 DB 연결 정보가 없으면 대기로 표시.

성공 기준:
- 위 파일들이 실제로 존재해야 함.
- 각 파일에 상태표와 다음 행동이 있어야 함.
- outputs 보고서가 생성되어야 함.
- git status를 확인해야 함.
- 변경 파일을 커밋해야 함.
- 커밋 SHA를 보고해야 함.

커밋 메시지:
Add plugin and skill activation runbook

답변 형식:
핵심 결론
적용한 내용
실행 방법
검증 방법
남은 작업
```
