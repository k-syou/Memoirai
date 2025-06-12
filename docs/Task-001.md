# Task-001: 프로젝트 초기 설정 및 Docker 환경 구성

## 작업 내용

### 1. 프로젝트 기본 구조 설정
- 프론트엔드(web)와 백엔드(server) 디렉토리 구조 생성
- 각 디렉토리별 기본 설정 파일 구성
- 프로젝트 문서화 (README.md, Library.md)

### 2. 프론트엔드 설정
- React + Vite + TypeScript 기반 프로젝트 설정
- 주요 디렉토리 구조:
  ```
  web/
  ├── src/
  │   ├── components/    # 재사용 컴포넌트
  │   ├── pages/        # 페이지 컴포넌트
  │   ├── hooks/        # 커스텀 훅
  │   ├── services/     # API 서비스
  │   ├── stores/       # 상태 관리
  │   ├── types/        # TypeScript 타입 정의
  │   └── utils/        # 유틸리티 함수
  └── public/           # 정적 파일
  ```
- 핵심 라이브러리 설치 및 설정:
  - TypeScript
  - Tailwind CSS
  - React Query
  - React Router DOM
  - HeadlessUI/React
  - Axios

### 3. 백엔드 설정
- FastAPI + PostgreSQL 기반 프로젝트 설정
- 주요 디렉토리 구조:
  ```
  server/
  ├── app/
  │   ├── api/          # API 라우트
  │   ├── core/         # 설정 및 공통 모듈
  │   ├── models/       # 데이터베이스 모델
  │   ├── services/     # 비즈니스 로직
  │   └── schemas/      # Pydantic 스키마
  ├── tests/            # 테스트 코드
  └── alembic/          # DB 마이그레이션
  ```
- 데이터베이스 설정:
  - PostgreSQL 연결 설정
  - 환경 변수 기반 설정 관리

### 4. Docker 환경 구성
- 각 서비스별 Dockerfile 작성:
  - web: Node.js 개발 환경
  - server: Python FastAPI 환경
  - db: PostgreSQL 데이터베이스
- Docker Compose 설정:
  - 서비스 간 의존성 관리
  - 볼륨 설정으로 데이터 영속성 확보
  - 개발 환경 핫 리로드 지원

### 5. 환경 변수 설정
- 프론트엔드 (.env.local):
  ```
  VITE_API_URL=http://localhost:8000
  ```
- 백엔드 (.env):
  ```
  POSTGRES_SERVER=db
  POSTGRES_USER=postgres
  POSTGRES_PASSWORD=postgres
  POSTGRES_DB=memoirai
  POSTGRES_PORT=5432
  ```

## 주요 변경사항
1. Next.js에서 React + Vite로 전환
   - 이유: 단순 SPA 구조에 더 적합한 가벼운 환경 구성
   - 장점: 빠른 개발 서버, 간단한 설정

2. Docker 환경 구성
   - 개발 환경의 일관성 확보
   - 서비스 간 격리와 확장성 고려
   - 볼륨을 통한 데이터 영속성 관리

## 향후 개선사항
1. 프론트엔드
   - 컴포넌트 구조 상세 설계
   - 상태 관리 전략 수립
   - API 통신 로직 구현

2. 백엔드
   - 데이터베이스 스키마 설계
   - API 엔드포인트 정의
   - 인증/인가 시스템 구현

3. 인프라
   - 프로덕션 환경 Docker 설정
   - CI/CD 파이프라인 구성
   - 모니터링 시스템 도입 검토 

# 🛠️ 기술 스택 선정 이유 및 차별성

---

## 🖥️ Frontend: React + Vite + Tailwind CSS

### ✅ 선택 이유
- **React**
  - 컴포넌트 기반 UI 설계에 최적화
  - 광범위한 커뮤니티와 레퍼런스
  - 상태 관리, API 연동 등 유연한 구조
- **Vite**
  - CRA(Create React App) 대비 **빌드/핫리로딩 속도 압도적**
  - 최신 ES 모듈 지원, 개발 생산성 향상
- **Tailwind CSS**
  - 빠르고 일관된 UI 스타일링
  - 클래스 조합만으로도 빠른 프로토타이핑
  - 별도 CSS 파일 없이 유지보수 편리

### 💡 차별성
- React + Vite 조합은 **경량성**과 **생산성**을 동시에 확보
- Tailwind는 BEM/SASS 등 전통 방식 대비 **스타일 일관성과 속도**에서 우위
- Next.js 대비 **SSR이 필요 없는 SPA 서비스에 더 적합**

---

## ⚙️ Backend: FastAPI

### ✅ 선택 이유
- **비동기 처리가 기본 지원 (async/await)**
  - OpenAI API, 외부 STT 서비스 등과 연동 시 효율적
- **Pydantic 기반의 타입 안정성 + 데이터 검증**
  - 신뢰성 높은 API 개발 가능
- **Swagger 문서 자동 생성**
  - 협업 및 API 테스트에 매우 유리
- **경량 구조**
  - 1인 개발, 초기 MVP 설계에 적합

### 💡 차별성
- Django 대비 **설정이 간단하고 불필요한 기능이 없음**
- Flask 대비 **타입 안정성, 비동기 처리, 문서화 기능 우수**
- Node.js(Express) 대비 **코드의 명확성과 유지보수성 높음**

---

## 🗄️ Database: PostgreSQL

### ✅ 선택 이유
- **관계형 데이터 모델에 강력한 호환성**
  - 사용자-회의-할일 간 명확한 관계 표현 가능
- **텍스트 기반 데이터 처리 성능 우수**
  - 회의록, 요약, 검색 기능에 적합
- **JSON, 배열, Full-Text Search 등 다양한 기능 내장**
  - 구조화+유연한 쿼리 모두 처리 가능

### 💡 차별성
- MySQL 대비 **문자 인코딩 및 복잡 쿼리 처리 성능 우수**
- SQLite 대비 **다중 사용자 처리 및 확장성 뛰어남**
- MongoDB 대비 **정규화된 관계 표현 및 JOIN 성능 우수**

---

## 🌐 전체 조합의 장점

| 항목 | 내용 |
|------|------|
| 🧩 조합 최적화 | 경량 + 빠른 개발 + 유지보수 용이 |
| ⚡ 생산성 | 빠른 핫리로드, 타입 기반 API, 자동 문서화 |
| 🔒 신뢰성 | 안정적인 DB 설계 + 명확한 API 스펙 |
| 🎯 확장성 | SPA 구조 기반 → 모바일 앱(React Native)로 확장 용이 |
| 👩‍💻 포트폴리오 어필 | 최신 트렌드 기술 스택 기반, 코드와 구조 설계 모두 설명 가능 |

---

## ✅ 선택 요약

- 복잡한 설정 없이 **최소 노력으로 최대 효과**를 낼 수 있는 최신 웹 스택
- 실제 SaaS 서비스와 동일한 구조로, **포트폴리오의 실무 친화성 강화**
- 프론트엔드/백엔드/데이터베이스 모두 **서로 자연스럽게 연동되는 기술 조합**

