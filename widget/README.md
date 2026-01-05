# widgets

이 디렉토리는 **비즈니스 로직이 결합된 복합 UI 컴포넌트** 중, **여러 페이지에서 재사용되는** 컴포넌트를 관리합니다.

`pages`와 `shared`의 중간 단계로, `business-logic`의 훅을 직접 사용하여 데이터를 처리하고 UI를 렌더링할 수 있습니다. 

단, **단일 페이지에서만 쓰이는 컴포넌트는 이곳에 위치하지 않습니다.**

<br>

## 핵심 원칙 

1.  **재사용성 필수 (Must be Shared)**
    * **2개 이상의 페이지**에서 똑같은 기능과 UI가 사용될 때만 이곳에 작성합니다.
    * 한 페이지에서만 쓰인다면 해당 `pages` 폴더 내부의 `components` 폴더에 두는 것이 낫습니다.
2.  **스마트 컴포넌트 (Smart Component)**
    * `business-logic`의 커스텀 훅(React Query 등)을 import 하여 데이터를 스스로 핸들링할 수 있습니다.
3.  **기능 단위 그룹화**
    * `business-logic`과 동일하게 기능(Feature) 단위로 폴더를 구성합니다.

<br>

## 📂 폴더 구조

비즈니스 도메인별로 분류합니다.

```text
widget/
├── auth/                   # [기능] 인증 관련 위젯
│   ├── LoginForm.tsx       # (로그인 페이지, 모달 등에서 재사용)
│   └── UserProfile.tsx     # (헤더, 마이페이지 등에서 재사용)
├── segment/                # [기능] 세그먼트 관련 위젯
│   ├── SegmentListTable.tsx
│   └── SegmentFilter.tsx
└── common/                 # 범용 위젯
    └── GlobalSearchBar.tsx