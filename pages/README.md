# pages

이 디렉토리는 라우팅에 매핑되는 **실제 페이지들의 진입점**입니다.

이곳에서는 직접적인 비즈니스 로직을 구현하지 않으며,

 `business-logic`에서 로직을 가져오고 `shared`나 `widget`에서 UI를 가져와 조립하는 역할을 수행합니다.

<br>

## 핵심 원칙 

1.  **조립과 배치 (Composition)**
    * 복잡한 로직이나 스타일 정의보다는, 이미 만들어진 로직(Hooks)과 컴포넌트를 배치하여 화면을 구성하는 데 집중합니다.
2.  **라우팅 매핑 (Routing)**
    * 폴더 구조는 URL 라우팅 구조와 직관적으로 매치되도록 구성합니다.
3.  **로직 위임 (Delegate Logic)**
    * 데이터 페칭, 폼 핸들링 등의 구체적인 코드는 `business-logic`으로 위임하고, 페이지는 결과값만 받아 렌더링합니다.

<br>

## 📂 폴더 구조 

라우팅 경로에 맞춰 폴더를 중첩하여 구성합니다.

```text
pages/
├── login/                  # /login
│   └── index.tsx           # 로그인 페이지 진입점
├── dashboard/              # /dashboard
│   ├── index.tsx           # 대시보드 메인
│   └── components/         # (선택) 이 페이지에서만 쓰이는 전용 컴포넌트
└── segment/                # /segment
    ├── list/               # /segment/list
    └── detail/             # /segment/detail
