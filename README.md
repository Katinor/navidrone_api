# navidrone_api

---

이 레포지토리는 경북대학교 전자공학부 종합설계프로젝트(캡스톤디자인 프로젝트) 팀 네비드론의 API 설명문서입니다.

**Table of Contents**

- [Usage](#usage)
  - [Legacy API](#legacy-api)
    - [Find target](#find-target)
  - [New API](#new-api)
	- [Create account](#create-account)
    - [Login](#login)
      - [Login by ID](#login-by-id)
      - [Login by token](#login-by-token)

## Usage

### Lagacy API

 - 이 API는 기존 작물정보만을 출력하는 기능을 가지고 있습니다.
 - 입력은 URL의 엔드포인트로 받습니다. 즉, <변수>가 주소 뒤에 추가되면 됩니다.
 - 출력은 JSON 객체로 이루어집니다.

#### Find target

경로 : /api/<작물이름>

출력 :

| 라벨 | 타입 | 설명 |
| ---- | ---- | ----------- |
| name | string | 작물이 데이터베이스에 저장되어있는 실제 이름입니다. |
| temp | int | 해당 작물의 적정온도입니다. |
| mois | int | 해당 작물의 적정습도입니다. |
| illu | int | 해당 작물의 적정조도입니다. |
| desc | int | 해당 작물의 적정 미세먼지농도입니다. |


### New API

 - 이 API는 사용자 계정정보 관리기능이 함께 존재합니다.
 - 입력은 HTTP 유입 요청 데이터로 이루어집니다. 즉 `엔드포인트/?a=~&b=~&...` 방식으로 입력합니다.
 - 출력은 JSON 객체로 이루어집니다.
 - 에러코드가 `000`일 경우 기본적으로 에러없음입니다.
 - 에러코드는 `string` 입니다.

#### Create account

입력 :

| 라벨 | 타입 | 설명 |
| ---- | ---- | ----------- |
| char_id | string | 계정의 ID |
| name | string | 계정 사용자의 닉네임 |
| pwd | string | 계정의 비밀번호 |

출력 :

| 라벨 | 타입 | 설명 |
| ---- | ---- | ----------- |
| errcode | string | 에러코드 |
| msg | string | 서버측 응답 스트링 |

에러코드 :

| 코드 | 설명 |
| ---- | ----------- |
| 101 ~ 103 | char_id / name / pwd 누락 |
| 105 | 이미 해당 id가 존재함 |
| 106 | 입력값이 너무 큼 |
| 107 | 입력값에 허가되지 않은 문자가 포함됨 |