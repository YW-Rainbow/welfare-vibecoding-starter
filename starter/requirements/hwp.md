# HWP 서식을 다루는 앱의 설계 기준

> 출처·최신판: https://github.com/YW-Rainbow/welfare-vibecoding-starter
> 사회복지 현장의 공문, 사업계획서, 결과보고서, 회의록, 지자체 제출 서식은 대부분 HWP나 HWPX 파일입니다. 이 문서는 그 서식을 앱과 연결하는 방법을 정합니다. 도구는 오픈소스 [rhwp](https://github.com/edwardkim/rhwp)(MIT)와 그 위에 만든 [rhwp-studio](https://github.com/dreamworker0/rhwp-studio)(MIT)를 기준으로 설명합니다. 두 프로젝트는 빠르게 바뀌므로 API 이름과 제약은 사용 시점에 해당 저장소에서 다시 확인합니다.

## 이 문서를 적용하는 시점

- `../workflow.md`의 "추천에 필요한 정보" 13번에서 기관 서식이 HWP 파일이라고 확인했을 때
- 기존 HWP 양식을 앱으로 바꾸려 할 때
- 앱의 결과를 HWP로 내려받거나 Google Drive에 HWP로 저장해야 할 때

`print.md`의 인쇄·엑셀 기준과 함께 적용합니다.

## 원칙: 원본은 데이터이고 HWP는 출력물입니다

지금 현장에서는 데이터가 HWP 파일 안에 들어 있습니다. 같은 이용자의 이름과 생년월일이 서식 수십 개에 반복 입력되고, 집계할 때는 파일을 열어 눈으로 옮겨 적습니다. 앱을 만들 때 이 순서를 뒤집어야 합니다.

- 데이터는 앱의 데이터베이스나 시트에 한 번만 저장합니다. `../data/ssot.md`의 단일 원본 원칙을 따릅니다.
- HWP는 그 데이터를 기관 서식에 맞춰 만든 결과물입니다. 필요할 때마다 다시 만들 수 있어야 합니다.
- 생성한 HWP 파일을 나중에 다시 읽어 데이터로 쓰지 않습니다. 파일을 고치면 데이터와 어긋납니다.

이 원칙을 지키지 않으면 앱은 파일을 정리하는 도구가 되고, 집계와 중복 제거가 다시 사람 몫으로 돌아갑니다.

## 구현 방식: 누름틀 서식에 데이터를 채웁니다

1. 기관 서식 HWP에서 값이 들어갈 자리에 **누름틀**(필드)을 만들고 이름을 붙입니다. 한글 프로그램에서 직접 하거나 rhwp-studio 편집기에서 할 수 있습니다. 누름틀 이름은 앱의 데이터 항목 이름과 같게 합니다.
2. 앱은 `@rhwp/core`(WebAssembly)를 브라우저에서 로드해 서식 파일을 열고, 필드 목록을 읽고, 이름으로 값을 채운 뒤 HWP 바이트로 내보냅니다. rhwp의 WASM API에는 필드 목록 조회, 이름으로 값 설정, HWP 내보내기 함수가 있고 HWPX 저장도 지원합니다.
3. 만든 파일은 사용자가 내려받거나 Drive에 올립니다. 처리가 모두 브라우저 안에서 끝나므로 이용자 정보가 앱 서버 밖으로 나가지 않습니다.
4. 반복되는 표(참석자 명단, 회기별 기록)는 누름틀의 반복 필드나 표 셀 좌표로 값을 쓰는 방식을 rhwp 문서에서 확인해 사용합니다.

법정서식은 형식을 바꾸지 않고 이 방식으로 채우기만 합니다. `../workflow.md`의 법정서식 원칙과 같습니다.

PDF가 필요하면 브라우저 인쇄로 만들거나, 서버가 있는 경로에서는 rhwp CLI의 PDF 내보내기를 사용합니다. 종이로 낼 서식은 `print.md`의 기준을 먼저 충족해야 합니다.

## AI가 기존 HWP 양식을 읽게 하는 방법

양식 점검(`../assess/form-audit.md`)이나 데이터 항목 설계를 할 때, AI에게 양식을 말로 설명하는 대신 파일을 직접 읽게 할 수 있습니다. rhwp에는 MCP 서버가 내장되어 있어 Claude Code 같은 에이전트형 도구가 HWP를 열고 검색하고 필드를 채울 수 있습니다.

1. rhwp 릴리스에서 운영체제에 맞는 실행 파일을 받아 PATH에 둡니다. 소스 빌드는 필요하지 않습니다.
2. 앱 저장소의 `.mcp.json`에 다음을 추가합니다.

```json
{ "mcpServers": { "rhwp": { "command": "rhwp", "args": ["mcp-serve"] } } }
```

3. AI는 `hwp_info`로 문서 규모를 보고, `hwp_fields`로 누름틀 목록을 읽고, `hwp_search`로 항목 위치를 찾고, `hwp_export_svg`로 페이지 모양을 확인합니다. 이 정보로 데이터 항목, 반복 구조, 출력 요건을 뽑아 DECISION.md와 데이터 설계에 반영합니다.

**빈 양식만 제공합니다.** 채워진 문서에는 이용자와 직원의 개인정보가 들어 있습니다. `../rules/agentic.md`의 "운영 데이터를 에이전트에게 제공하지 않습니다"가 그대로 적용됩니다.

## 플랫폼 경로별 가능 여부

| 경로 | HWP 생성 | 비고 |
|---|---|---|
| B. 로컬 퍼스트 | 브라우저에서 `@rhwp/core`로 생성 | 서버가 없어 가장 단순합니다. 내려받기로 끝납니다 |
| C. GAS+시트 | 브라우저 쪽 HTML에서 생성한 뒤 `google.script.run`으로 바이트를 넘겨 DriveApp으로 저장 | GAS 웹앱은 응답 헤더를 설정할 수 없습니다. 아래 "확인 필요" 1번 |
| A·D. Cloudflare Pages | 브라우저에서 생성. `_headers` 파일로 헤더 설정 가능 | 헤더가 다른 도메인의 스크립트와 이미지 로딩을 막을 수 있습니다. 아래 1번 |
| A'. Cloud Run | 서버에 rhwp CLI 실행 파일을 두고 채우기·PDF 변환 | 서버가 이용자 정보를 처리하므로 리전과 로그 기준을 그대로 적용합니다 |

## Google Drive와 함께 쓰는 방법

많은 기관이 Google Workspace와 Drive를 씁니다. 새로 만들 필요가 없는 것과 만들어야 하는 것을 구분합니다.

- **Drive에서 HWP 열기·편집·저장**은 rhwp-studio가 이미 합니다. Google Workspace Marketplace에 등록되어 있어 기관 관리자가 설치하면 직원 전체가 Drive에서 "연결 앱으로 열기"로 씁니다. 로컬 HWP와 웹에서 내려받은 HWP를 브라우저에서 바로 열고 편집하고 인쇄하는 것은 rhwp의 [크롬 확장](https://chromewebstore.google.com/detail/pgakpjflombjmehnebnbpnalhegaanag)과 엣지·파이어폭스 확장이 합니다. 이 두 가지는 앱에 넣지 않고 안내만 합니다.
- **앱 안에서 HWP 편집기를 보여 주려면** `@rhwp/editor`를 iframe으로 넣고 Drive API로 파일을 읽고 씁니다. 앱이 만든 파일과 사용자가 직접 고른 파일만 다루는 `drive.file` 범위를 사용하면 Google의 앱 심사가 가볍습니다. 파일 선택은 Google Picker를 씁니다.
- **기관이 Workspace를 쓰면** Google Cloud의 OAuth 동의 화면을 "내부용"으로 설정할 수 있습니다. 내부용 앱은 기관 계정만 로그인할 수 있고 Google의 심사를 받지 않으므로 Drive 전체를 다루는 범위도 쓸 수 있습니다. 경로 C에서 가장 짧은 길입니다.
- **Google Docs 문서를 앱 안에서 편집하는 것은 되지 않습니다.** Google이 편집 화면을 다른 사이트에 넣는 것을 허용하지 않습니다. 새 탭으로 열어 줍니다. 파일 목록, 만들기, 이동, 삭제는 Drive API나 GAS의 DriveApp으로 합니다.
- 생성한 HWP를 Drive에 저장할 때는 저장 폴더, 공유 권한, 보존 기간을 정하고 `../../ops/destruction-log.md`의 파기 대상에 포함합니다. 파일 안에 이용자 정보가 있기 때문입니다.

## 확인 필요

이 문서를 쓰는 시점(2026년 9월)에 실제로 돌려 보지 않은 항목입니다. 첫 앱을 만들 때 확인하고, 결과는 원본 저장소에 이슈나 PR로 알려 주세요(`../../.github/CONTRIBUTING.md`). 앱 저장소 안의 `starter/`는 고치지 않습니다.

1. `@rhwp/core`만 사용할 때도 rhwp-studio처럼 `Cross-Origin-Opener-Policy`와 `Cross-Origin-Embedder-Policy` 헤더가 필요한지. 필요하다면 GAS 웹앱에서는 쓸 수 없고, Cloudflare Pages에서는 Google API 스크립트 로딩과 충돌할 수 있습니다.
2. GAS 웹앱의 HTML에서 `@rhwp/core`를 CDN으로 로드해 실행할 수 있는지.
3. 반복 표 채우기가 누름틀 반복 필드로 충분한지, 표 셀 좌표 쓰기가 필요한지.
4. HWPX로 저장한 파일을 지자체 시스템이 그대로 받는지. 받지 않으면 HWP로 저장합니다.

## 관련 문서

- `print.md`: 종이·엑셀 출력 기준
- `../data/ssot.md`: 단일 원본과 이용자 ID
- `../assess/form-audit.md`: 양식 점검
- `../assess/form-to-app.md`: HWP 양식에서 앱까지 가는 절차
- `../rules/agentic.md`: 에이전트에게 운영 데이터를 주지 않는 원칙
