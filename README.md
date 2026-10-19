# 🤖 E-Commerce Issue Resolver Agent

## 📖 Overview
E-Commerce Issue Resolver Agent는 CS(고객 서비스) 팀에서 접수된 쇼핑몰 연동 및 시스템 에러 문의를 개발팀으로 이관하는 과정을 자동화하고 해결하는 AI 에이전트입니다. Jira API와 GitHub API를 활용하여 이슈의 원인을 분석하고, 가이드 제공부터 코드 수정 PR(Pull Request) 생성까지 Agentic Workflow를 통해 처리합니다.

## ✨ Key Features (Scenarios)

1. **사용자 과실 및 설정 오류 자동 안내 (Scenario 1)**
   - Jira에 등록된 이슈 내용과 에러 로그를 분석합니다.
   - 코드 수정이 필요 없는 솔루션 오사용 건으로 판별될 경우, 해결 가이드를 Jira 댓글로 작성하고 이슈 상태를 `Done(Close)`으로 자동 변경합니다.

2. **AI 바이브 코딩 기반 자동 PR 생성 (Scenario 2)**
   - 코드 수정이 필요한 버그로 판별될 경우, 해당 쇼핑몰 연동 파트의 코드를 분석합니다.
   - 새로운 브랜치를 생성하여 코드를 수정한 뒤 GitHub에 Pull Request를 자동으로 업로드합니다.
   - 리뷰어의 피드백 코멘트가 달리면 이를 반영하여 추가 커밋을 수행합니다.

3. **외부 쇼핑몰 확인 필요 건 분기 처리 (Scenario 3 - Human in the loop)**
   - 에이전트가 자체 해결할 수 없는 외부 쇼핑몰 API 응답 지연 및 정책 변경 건을 식별합니다.
   - 쇼핑몰 측에 문의할 내용 초안을 작성하여 Jira에 남기고 대기(Hold) 상태로 전환합니다.
   - 담당자가 쇼핑몰 답변을 업데이트하면 내용을 분석하여 Scenario 1 또는 2의 과정을 이어서 수행합니다.

4. **CI/CD 연동 자동화**
   - GitHub Actions 배포 파이프라인과 연동하여 배포가 완료되면 연결된 Jira 티켓을 자동으로 Close 처리합니다.

## 🛠 Tech Stack
- **Language**: TypeScript
- **AI Framework**: LangGraph / LangChain (에이전트 오케스트레이션)
- **Integration**: 
  - Jira REST API (이슈 트래킹 및 상태 관리)
  - GitHub API / GitHub Actions (PR 생성 및 배포 파이프라인 연동)
  - GraphQL (필요 시 데이터 쿼리용)

## 🚀 Getting Started

### Prerequisites

**[공통]**
- Node.js (v18+) 또는 .NET SDK
- [Cursor IDE](https://cursor.sh/) (AI 바이브 코딩 권장 편집기)
- Git

**[Mac 환경]**
- [Homebrew](https://brew.sh/) (패키지 관리용)

**[Windows 환경]**
- Windows 10/11
- [winget](https://learn.microsoft.com/ko-kr/windows/package-manager/winget/) 또는 Chocolatey (패키지 관리용, 선택 사항)
- *Tip: 원활한 개발 및 스크립트 실행을 위해 [WSL2 (Windows Subsystem for Linux)](https://learn.microsoft.com/ko-kr/windows/wsl/install) 환경에서의 실행을 권장합니다.*

### Installation
```bash
# 1. Repository 클론 (Mac 터미널 / Windows PowerShell 또는 WSL 공통)
git clone [https://github.com/kimnamhyeon0112/ecommerce-issue-resolver-agent.git](https://github.com/kimnamhyeon0112/ecommerce-issue-resolver-agent.git)
cd ecommerce-issue-resolver-agent

# 2. 패키지 설치
npm install
```

## 🗺 Roadmap
[ ] Phase 1: Jira API 연동 및 RAG 기반 에러 티켓 분류 모델 구축

[ ] Phase 2: 시나리오 1 (가이드 댓글 작성 및 자동 Close) 파이프라인 완성

[ ] Phase 3: 시나리오 2 (GitHub API 연동, 코드 분석 및 PR 자동 생성) 구현

[ ] Phase 4: 시나리오 3 (쇼핑몰 문의 분기 및 Human-in-the-loop) 적용

[ ] Phase 5: GitHub Actions 연동 테스트 및 배포 자동화
