# Memoirai Web Client

회의록 자동 요약 및 할일 추출 서비스의 웹 클라이언트

## 기술 스택

- React 18
- TypeScript
- Vite
- Tailwind CSS
- React Query
- React Router DOM
- Headless UI
- Heroicons

## 시작하기

1. 의존성 설치
```bash
npm install
```

2. 개발 서버 실행
```bash
npm run dev
```

3. 프로덕션 빌드
```bash
npm run build
```

## 프로젝트 구조

```
web/
├── src/
│   ├── assets/        # 이미지, 폰트 등 정적 파일
│   ├── components/    # 재사용 가능한 컴포넌트
│   ├── hooks/        # 커스텀 훅
│   ├── pages/        # 페이지 컴포넌트
│   ├── services/     # API 통신 로직
│   ├── stores/       # 상태 관리
│   ├── types/        # TypeScript 타입 정의
│   └── utils/        # 유틸리티 함수
├── public/           # 정적 파일
└── docs/            # 프로젝트 문서
```

## 주요 기능

- 회의록 업로드 및 관리
- 회의록 자동 요약
- 할일 목록 추출 및 관리
- 실시간 협업 기능

## 스타일 가이드

- Tailwind CSS를 사용한 유틸리티 우선 스타일링
- Headless UI 컴포넌트를 활용한 접근성 고려
- Heroicons를 통한 일관된 아이콘 시스템

## 개발 가이드

### 코드 품질

```bash
# 린트 검사
npm run lint

# 타입 검사
npm run typecheck
```

### 컴포넌트 개발

- 함수형 컴포넌트와 훅 사용
- Props 타입 명시적 정의
- 컴포넌트 단위 테스트 작성

### API 통신

- React Query를 사용한 서버 상태 관리
- Axios 인스턴스를 통한 일관된 API 호출
- 타입 안전한 API 응답 처리

## 환경 설정

```bash
# 개발 환경
npm run dev

# 테스트 환경
npm run test

# 프로덕션 빌드
npm run build
npm run preview
```

## 브라우저 지원

- Chrome (최신 2개 버전)
- Firefox (최신 2개 버전)
- Safari (최신 2개 버전)
- Edge (최신 2개 버전)

## 라이선스

MIT
