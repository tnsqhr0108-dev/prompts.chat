# AGENTS.md

Repository: `tnsqhr0108-dev/prompts.chat`
Primary branch: `main`

## Mandatory startup checks

Before answering, editing, claiming status, or saying a task is complete, inspect or run:

```bash
pwd
git branch --show-current
git rev-parse HEAD
git status --short
find . -maxdepth 3 -type f | sort
```

Also read and apply these repository policy files when they exist:

- `docs/CODEX_CLOUD_RUNBOOK.md`
- `docs/CODEX_ANSWER_QUALITY_POLICY.md`

## Actual application rule

These rules apply when the Codex task is opened with repository `tnsqhr0108-dev/prompts.chat` and branch `main` selected.
If another repository is needed, inspect that repository directly and cite the evidence.

## Answer quality rules

- 실제 저장소 파일과 터미널 결과를 기준으로 답변한다.
- 브랜치명, 파일명, 출력물, 로그, 완료 여부를 추측하지 않는다.
- 예상 파일, 로그, 테스트 결과, 산출물이 실제로 존재하지 않으면 완료라고 말하지 않는다.
- 검사하지 않은 항목은 통과가 아니라 `검수하지 못함`으로 보고한다.
- 중첩 clone 저장소, `.venv`, 캐시, 임시파일은 커밋하지 않는다.
- 큰 변경보다 작고 검증 가능한 변경을 우선한다.
- 사용자에게 설명할 때는 기본적으로 한국어로 답변한다.

## Completion rule

A task is complete only when the expected changed files, logs, generated outputs, or test results actually exist in this repository.
<!-- BEGIN MASTERBOOK OVERLAY -->

# MasterBook / Codex / AGBROWSE / Jawcode Instructions

This repository is connected to the MasterBook workflow.

Default response structure:
1. 계획
2. 계획검증
3. 작업실행
4. 작업검증
5. Harness-600 감점 평가
6. GAN-like 생성자-판별자-검토자 개선 루프
7. 다음 작업

Core MasterBook math flow:
조건 읽기 -> 반응 선택 -> 첫 식 세우기 -> 계산 -> 검산 -> 변형 대응

Rules:
- Do not fabricate official CSAT, mock exam, or EBS materials.
- Keep source metadata when using official exam material.
- Never commit API keys, GitHub tokens, passwords, cookies, browser sessions, Codex sessions, or .env files.
- Never commit ~/.browser-agent, ~/.codex, ~/.config/gh/hosts.yml, or local credential files.
- Do not claim completion without command logs and verification.
- For GitHub work, only say complete after actual commit, push, pull request, or verification.
- Use Codex, AGBROWSE, browser, web-ai, vision-click, and Jawcode only when useful and safe.
- Ads, marketing, and Ads Manager are excluded.

Required MasterBook components when relevant:
- RAG
- embedding-based semantic search
- official source registry
- problem metadata schema
- wrong-answer pattern analysis
- variant problem generation
- mathematical verification
- Harness-600 scoring
- reproducible logs
- GitHub-based version control

<!-- END MASTERBOOK OVERLAY -->
