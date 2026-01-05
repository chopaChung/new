# pages

이 디렉토리는 라우팅에 매핑되는 **실제 페이지들의 진입점**이자, **해당 페이지에 특화된 UI를 구현하는 곳**입니다.

`business-logic`에서 데이터를 받아오고, `shared`나 `widget`의 공용 컴포넌트를 조립합니다.

또한, 다른 페이지에서 재사용되지 않는 페이지 고유의 UI(Feature UI)는 이곳에서 직접 정의하고 관리합니다.

<br>

## 핵심 원칙 

1.  **라우팅 매핑 (Routing)**
    * 폴더 구조는 URL 구조와 직관적으로 일치해야 합니다.

2.  **페이지 전용 UI 소유 (Colocation)**
    * "재사용되지 않는 UI는 페이지가 소유한다"는 원칙을 따릅니다.
    * 특정 페이지에서만 사용되는 컴포넌트(복잡한 테이블, 전용 폼 등)는 억지로 `widget`으로 보내지 않고,
    
      해당 페이지 폴더 내부의 `components` 디렉토리에서 관리합니다.

3.  **조립과 위임 (Composition & Delegation)**
    * **Logic**: 데이터 페칭 및 비즈니스 로직은 `business-logic`으로 위임합니다.
    * **UI**: 공용 UI는 `widget/shared`에서 가져오고, 전용 UI는 내부에서 구현하여 이들을 조립합니다.

<br>

## 📂 폴더 구조 

페이지별로 독립적인 **작은 애플리케이션**처럼 구성합니다.

```text
pages/
├── login/                  # [URL: /login]
│   └── index.tsx
│
├── dashboard/              # [URL: /dashboard]
│   ├── index.tsx           # 대시보드 조립 (Layout + Components)
│   └── components/         # ⭐️ [핵심] 이 페이지 전용 UI 모음
│       ├── DashboardChart.tsx  # (다른 곳에서 안 씀 -> 여기서 관리)
│       └── RecentLogTable.tsx  # (다른 곳에서 안 씀 -> 여기서 관리)
│
└── segment/                # [URL: /segment]
    ├── list/
    │   └── index.tsx
    └── detail/
        └── index.tsx
