# business-logic

이 디렉토리는 애플리케이션의 **순수 비즈니스 로직**을 **기능(Feature) 단위**로 관리하는 핵심 영역입니다.

UI 렌더링 코드(JSX)는 절대 포함하지 않으며, 데이터 처리, API 통신, 상태 관리 등 기능적 요구사항에만 집중합니다. 

특히 Server State 동기화(React Query)를 최우선으로 하며, 전역 상태 관리(Zustand)는 최소화하는 것을 원칙으로 합니다.

<br>

## 핵심 원칙 

1.  **기능 단위 그룹화 (Feature-First)**
    * 파일의 기술적 분류(hook, util)가 아닌 비즈니스 도메인(기능)별로 폴더를 생성하여 응집도를 높입니다.
    * 예: `auth/`, `segment/`, `dashboard/`

2.  **Zero UI (No JSX)**
    * 이곳에는 `<div>`, `<button>` 등 UI 태그가 절대 포함되지 않습니다.
    * 오직 `Hooks`, `API Services`, `Utils`, `Types` 등 순수 로직만 존재합니다.

3.  **React Query 중심의 상태 관리**
    * 비동기 데이터 관리와 상태 동기화는 **React Query**를 주력으로 사용합니다.
    * **Zustand**와 같은 전역 스토어는 꼭 필요한 경우(복잡한 클라이언트 전용 상태)에만 제한적으로 사용합니다.

4.  **View와의 철저한 분리**
    * 이곳의 로직은 주로 **`pages`** 폴더에서 호출하여 사용합니다.
    * 해당 로직이 포함된 UI가 **여러 페이지에서 공통으로 사용될 경우**에만 **`widget`** 폴더로 UI 구성을 위임합니다.

<br>

## 📂 폴더 구조 

기능명(Feature) 폴더 내부에 해당 기능을 수행하기 위한 로직 파일들이 응집해 위치합니다.

```text
business-logic/
├── auth/                   # [기능] 인증
│   ├── useLogin.ts         # 로그인 커스텀 훅 (useMutation 포함)
│   ├── authApi.ts          # API 호출 함수
│   └── auth.types.ts       # 타입 정의
│
├── segment/                # [기능] 세그먼트
│   ├── useSegmentList.ts   # 세그먼트 목록 조회 훅 (useQuery)
│   ├── useSegmentAction.ts # 세그먼트 생성/수정 로직
│   └── segmentUtils.ts     # 데이터 가공 및 포맷팅 순수 함수
│
└── common/                 # [공통] 범용 로직
    ├── useModal.ts
    └── dateUtils.ts
