# AI 규칙 파일: Google Cloud·Firebase 서울 리전(경로 A'·F)

> 출처·최신판: https://github.com/YW-Rainbow/welfare-vibecoding-starter
> 적용 대상: Google Cloud 또는 Firebase를 사용해 개인정보 앱을 운영하며 리전, 권한, 비용을 관리할 담당자가 있는 기관
> 기준일: 2026-09
> **AI에게**: 사용자는 개발 지식이 없다고 가정합니다. 전문용어가 처음 나오면 `glossary.md`의 설명을 참고해 한 문장으로 풀어서 설명하세요. 이 파일과 `rules/agentic.md`를 함께 적용하세요.

## 1. 요구사항에 따라 구성을 선택합니다

GCP를 선택했다고 모든 서비스를 사용할 필요는 없습니다. 오프라인 동기화와 실시간 화면이 중요한 앱은 Firebase 구성이 적합하고, SQL 집계나 서버 중심의 업무 규칙이 중요한 앱은 Cloud Run과 Cloud SQL 구성이 적합합니다.

| 요구사항 | 권장 구성 |
|---|---|
| 방문·외근 중 오프라인 입력과 자동 동기화 | Firebase Hosting + Firebase Auth + Firestore + Cloud Storage + Cloud Functions |
| 실인원·연인원, 연도별 비교, 여러 테이블의 복잡한 집계 | Cloud Run + Cloud SQL for PostgreSQL + Cloud Storage + Firebase Auth 또는 Identity Platform |
| 공개 페이지와 간단한 서버 API | 정적 호스팅 + Cloud Run |
| 문서형 데이터는 필요하지만 서버 API에서만 접근 | Cloud Run + Firestore(Admin SDK) |

Firestore는 문서형 데이터베이스이므로 `COUNT(DISTINCT ...)` 같은 관계형 집계를 직접 처리하기 어렵습니다. 장기 실적 분석과 복잡한 조인이 핵심이면 Cloud SQL을 사용하고, Firestore 데이터를 BigQuery로 내보내는 구성을 추가할 때는 비용과 운영 대상을 함께 검토합니다.

## 2. 개인정보를 처리하는 리전을 서울로 고정합니다

- Cloud Run, Cloud Run functions 또는 Cloud Functions for Firebase, Firestore, Cloud Storage는 지원 여부를 확인한 뒤 `asia-northeast3`(서울)에 생성합니다.
- 함수의 리전을 기본값에 맡기지 않습니다. 코드의 `region` 옵션과 클라이언트의 함수 호출 위치를 모두 `asia-northeast3`로 지정합니다.
- Firestore와 Cloud Storage의 위치는 운영 중 변경하기 어렵거나 새 리소스로 이관해야 하므로 프로젝트를 만들 때 먼저 결정합니다.
- Cloud Run과 함수는 Firestore·Cloud Storage와 같은 리전을 사용해 데이터의 리전 간 이동, 지연 시간, 네트워크 비용을 줄입니다.
- 서울 리전에 저장하더라도 해외 운영 인력의 접근과 지원 과정까지 자동으로 국내 처리만 보장되는 것은 아닙니다. 개인정보 처리방침과 국외이전 여부는 계약과 서비스별 데이터 처리 문서를 확인해 판단합니다.

## 3. 인증과 기관별 데이터 격리를 분리해서 구현합니다

로그인 성공은 데이터 접근 권한을 의미하지 않습니다. 모든 기관 데이터에는 `organizationId`를 저장하고 클라이언트, Security Rules, 서버 함수에서 각각 권한을 확인합니다.

1. Firebase Auth 또는 Identity Platform에서 사용자를 인증합니다.
2. Custom Claims에는 `organizationId`와 최소한의 역할만 저장합니다. 역할을 변경하면 기존 토큰이 갱신되기 전까지 이전 값이 남을 수 있으므로 서버의 사용자 문서도 함께 확인할지 결정합니다.
3. 클라이언트의 모든 Firestore 쿼리에 `where('organizationId', '==', currentOrganizationId)` 조건을 포함합니다. Firestore Security Rules는 조회 결과를 필터링하지 않으므로 조건이 없는 쿼리는 권한 오류가 발생하거나 잘못된 규칙에서 다른 기관 데이터가 노출될 수 있습니다.
4. Firestore와 Storage Rules에서 기존 문서와 새 문서의 `organizationId`가 로그인 사용자의 기관과 같은지 확인합니다.
5. Cloud Run과 Cloud Functions에서 Admin SDK를 사용하면 Security Rules가 적용되지 않습니다. 서버 함수가 사용자 UID, 기관, 역할, 대상 데이터의 기관을 다시 검증해야 합니다.

기관 분리 테스트에는 최소한 다음 계정을 사용합니다.

- 같은 기관의 일반 직원
- 같은 기관의 관리자
- 다른 기관의 직원
- 로그인하지 않은 사용자

각 계정으로 조회·생성·수정·삭제를 테스트하고 다른 기관 데이터 접근이 거부되는지 확인합니다.

## 4. Firestore와 Storage Rules는 기본 거부로 시작합니다

- 넓은 wildcard 허용 규칙을 만들지 않고 컬렉션과 파일 경로별로 필요한 작업만 허용합니다. Firestore Rules는 여러 `allow` 조건 중 하나라도 참이면 요청을 허용하므로 뒤에 작성한 좁은 규칙이 앞의 넓은 허용을 취소하지 못합니다.
- 생성 요청에는 `request.resource.data.organizationId`, 기존 문서의 조회·수정·삭제에는 `resource.data.organizationId`를 확인합니다.
- 클라이언트가 수정할 수 있는 필드를 제한하고 역할, 기관 ID, 승인 상태 같은 권한 필드를 임의로 바꾸지 못하게 합니다.
- Storage는 `organizations/{organizationId}/...`처럼 기관 ID가 포함된 경로를 사용합니다. 파일 크기와 `contentType`을 검사하고 개인정보 파일은 public으로 제공하지 않습니다.
- Rules를 변경하면 Firebase Emulator Suite에서 같은 기관, 다른 기관, 비로그인 사용자의 허용·거부 테스트를 실행합니다. Rules 배포는 테스트 통과 뒤에만 진행합니다.
- App Check는 자동 요청과 남용을 줄이는 보조 수단으로 사용할 수 있지만 사용자 인증과 기관별 권한 검사를 대신하지 않습니다.

## 5. Cloud Run과 Cloud Functions의 서버 권한을 제한합니다

- Cloud Run 서비스는 기본적으로 인증된 호출만 허용합니다. 공개 API가 필요한 경우 공개할 endpoint를 분리하고 입력값 검증, rate limit, CORS를 별도로 적용합니다.
- 서비스 계정에는 실행에 필요한 IAM 역할만 부여합니다. 프로젝트 Owner나 Editor 역할을 런타임 서비스 계정에 부여하지 않습니다.
- API 키, 외부 서비스 토큰, 암호화 키는 Secret Manager에 저장합니다. `.env`는 로컬 개발용으로만 사용하고 저장소와 빌드 로그에 포함하지 않습니다.
- callable function과 HTTP endpoint는 클라이언트가 전달한 `organizationId`를 신뢰하지 않고 인증 토큰과 서버의 사용자 정보를 기준으로 결정합니다.
- Firestore·Pub/Sub·Storage 트리거는 같은 이벤트를 두 번 이상 전달할 수 있으므로 멱등성을 보장합니다. 이벤트 ID나 업무 ID를 저장해 중복 처리, 중복 알림, 중복 결제를 방지합니다.
- 새 Cloud Function은 진입점에서 export되었는지 확인하고 배포 후 실제 리전을 조회합니다. 기본 리전으로 배포되었다고 가정하지 않습니다.

## 6. 입력값과 동시성을 서버에서 검증합니다

- 클라이언트의 TypeScript 타입만 믿지 않고 Zod, JSON Schema 등 런타임 스키마로 서버 입력값을 검증합니다.
- 중복 예약, 순번 발급, 잔여 수량, 누적값처럼 동시에 수정될 수 있는 데이터는 Firestore transaction 또는 Cloud SQL transaction으로 처리합니다.
- 외부 API 호출이나 알림 발송 같은 되돌리기 어려운 작업은 먼저 dry-run으로 대상 수와 내용을 확인한 뒤 실행합니다.
- 대량 작업에는 최대 처리 건수, pagination, 재시도 횟수, 중복 방지 ID를 둡니다. 일부 실패가 발생했을 때 성공·실패 건과 재처리 방법을 반환합니다.

## 7. 접근 로그와 감사 로그를 서버에서 생성합니다

- 개인정보 조회·수정·삭제·출력 기록은 클라이언트가 아니라 Cloud Run, Cloud Functions, Firestore trigger 같은 서버 영역에서 생성합니다.
- 로그에는 사용자 UID, 기관 ID, 수행 업무, 대상 데이터 ID, 서버 시각, 결과를 기록합니다. 상담 내용과 전체 요청 본문은 로그에 저장하지 않습니다.
- 기록할 필드를 allowlist로 정해 비밀번호, 토큰, 주민등록번호, 상담 원문이 일반 로그와 오류 추적 서비스로 전송되지 않게 합니다.
- 감사 로그 컬렉션은 클라이언트의 수정과 삭제를 금지합니다. 법적 보관 기간이 지난 로그를 파기하는 별도 정책을 둡니다.
- Cloud Logging의 애플리케이션 로그와 개인정보 접근 로그는 목적과 보존 기간이 다르므로 분리합니다.

## 8. 파일과 데이터 삭제를 별도로 확인합니다

- Firestore 문서를 삭제해도 하위 subcollection은 자동으로 삭제되지 않습니다. 재귀 삭제 함수와 잔존 데이터 테스트를 구현합니다.
- Firestore 문서와 Cloud Storage 파일은 자동으로 함께 삭제되지 않습니다. 파일 경로를 메타데이터에 저장하고 삭제 함수에서 두 저장소를 모두 처리합니다.
- `retention_until` 또는 `expiresAt`을 저장하고 Firestore TTL이나 정기 함수로 보관 기간이 끝난 데이터를 삭제합니다. TTL은 즉시 실행되지 않을 수 있으므로 법적·업무상 정확한 파기 시점이 필요하면 별도 작업과 확인 절차를 사용합니다.
- 기관 탈퇴와 이용자 동의 철회는 Auth 계정, Firestore 문서, subcollection, Storage 파일, 파생 데이터, 백업의 처리 범위를 하나의 파기 계획에 포함합니다.

## 9. 백업과 복구를 별도 업무로 운영합니다

- Firestore의 scheduled backup 또는 export, Cloud SQL의 자동 백업과 point-in-time recovery를 요구사항에 맞게 설정합니다.
- Firestore 백업과 데이터베이스 export가 Cloud Storage의 첨부 파일을 포함한다고 가정하지 않습니다. 파일은 별도로 백업합니다.
- 백업 버킷도 서울 리전을 사용하고 운영 데이터와 다른 프로젝트나 제한된 서비스 계정으로 접근 범위를 분리합니다.
- 백업 성공 알림만 확인하지 말고 정기적으로 별도 프로젝트에 복구해 문서 수, 파일 수, 주요 관계를 검증합니다.

## 10. 비용과 운영 한도를 설정합니다

- Cloud Billing budget과 알림을 설정하되 budget이 과금을 자동으로 중단시키지 않는다는 점을 운영 문서에 기록합니다.
- Cloud Run과 Cloud Functions에는 적절한 `max instances`, timeout, memory를 설정해 오류나 반복 호출로 비용이 급증하는 범위를 제한합니다.
- Firestore 쿼리에는 pagination과 최대 조회 건수를 적용하고 N+1 쿼리를 피합니다. 반복 집계는 캐시나 정기 batch로 전환합니다.
- 정기 작업은 업무상 필요한 시간과 주기로 통합합니다. 작업별 스케줄러를 무분별하게 늘리지 않습니다.
- Firebase Blaze와 Google Cloud의 종량제 과금은 한도 초과 시 자동으로 정지되지 않을 수 있습니다. 결제 담당자, 알림 수신자, 비상 중단 절차를 `ops/handover.md`에 기록합니다.

## 11. 배포 전 체크리스트

- [ ] Firestore, Cloud Storage, Cloud Run, Cloud Functions가 의도한 서울 리전에 생성되었는가
- [ ] 다른 기관 계정과 비로그인 계정의 Firestore·Storage 접근이 차단되는가
- [ ] Cloud Run과 Cloud Functions가 사용자·기관·역할을 서버에서 다시 검증하는가
- [ ] Admin SDK 코드에 전체 컬렉션 조회나 기관 조건이 없는 쓰기가 남아 있지 않은가
- [ ] Firestore·Storage Rules Emulator 테스트가 통과하는가
- [ ] Secret Manager와 런타임 서비스 계정에 최소 권한이 적용되었는가
- [ ] 문서 삭제 뒤 subcollection과 Storage 파일이 남지 않는가
- [ ] 접근 로그에 필요한 항목만 남고 개인정보 원문과 시크릿은 제외되는가
- [ ] 백업에서 실제 복구했으며 최근 복구 테스트 일자를 기록했는가
- [ ] budget, 사용량 알림, `max instances`, 대량 작업 상한을 설정했는가
- [ ] 계정, 배포, 백업, 비용, 장애 대응 절차를 `ops/handover.md`에 작성했는가

## 차량 운행일지 프로젝트에서 참고한 구현 패턴

김종원 선생님의 [vehicle-drive-log](https://github.com/dreamworker0/vehicle-drive-log)는 React, Firebase Auth, Firestore, Storage, Cloud Functions를 사용하는 실제 운영 사례입니다. 도메인 로직을 그대로 복사하기보다 다음 구조와 테스트 방식을 참고합니다.

- [기관별 쿼리 검사](https://github.com/dreamworker0/vehicle-drive-log/blob/master/eslint-rules/require-organization-filter.js): Firestore 쿼리에서 `organizationId` 조건이 빠지면 lint 단계에서 실패하도록 만든 정적 검사
- [Firestore Rules](https://github.com/dreamworker0/vehicle-drive-log/blob/master/firestore.rules)와 [Rules 테스트](https://github.com/dreamworker0/vehicle-drive-log/blob/master/tests/firestore-rules.test.ts): 클라이언트 쿼리와 별도로 서버 측 기관 격리를 적용하고 Emulator에서 회귀 테스트
- [Storage Rules](https://github.com/dreamworker0/vehicle-drive-log/blob/master/storage.rules)와 [Storage 테스트](https://github.com/dreamworker0/vehicle-drive-log/blob/master/tests/storage-rules.test.ts): 파일 경로, 소유자, 크기, MIME type을 함께 검사
- [접근 로그 트리거](https://github.com/dreamworker0/vehicle-drive-log/blob/master/functions/src/handlers/triggers/auditLog.ts): 클라이언트가 아니라 서버 trigger에서 로그를 생성하고 기록할 필드를 제한
- [에이전트 작업 규칙](https://github.com/dreamworker0/vehicle-drive-log/blob/master/CLAUDE.md): 기관 ID 필터, 함수 export, 인덱스, 테스트, 배포 절차를 에이전트의 필수 규칙으로 관리

GCP의 리전과 제품 정책은 바뀔 수 있습니다. 배포 전에는 [Cloud Run 리전](https://cloud.google.com/run/docs/locations), [Cloud Functions 리전](https://firebase.google.com/docs/functions/locations), [Firestore 리전](https://firebase.google.com/docs/firestore/locations) 공식 문서에서 `asia-northeast3` 지원 여부를 다시 확인합니다.
