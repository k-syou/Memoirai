# Memoirai

회의록이나 회의 텍스트를 업로드하면 요약된 회의 내용과 할일 목록을 자동으로 생성해주는 서비스

## 기술 스택

### 프론트엔드
- Next.js 14
- TypeScript
- Tailwind CSS
- React

### 백엔드
- FastAPI
- PostgreSQL
- SQLAlchemy
- Alembic

## 시작하기

### 프론트엔드 실행
```bash
cd web
npm install
npm run dev
```

### 백엔드 실행
```bash
cd server
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```

## 환경 설정

### 프론트엔드 (.env.local)
```
NEXT_PUBLIC_API_URL=http://localhost:8000
```

### 백엔드 (.env)
```
DATABASE_URL=postgresql://user:password@localhost:5432/memoirai
SECRET_KEY=your-secret-key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

## 프로젝트 구조

```
memoirai/
├── web/                    # 프론트엔드
│   ├── src/
│   │   ├── app/           # Next.js 13+ App Router
│   │   ├── components/    # 재사용 가능한 컴포넌트
│   │   └── lib/          # 유틸리티 함수
│   └── public/            # 정적 파일
│
└── server/                # 백엔드
    ├── app/
    │   ├── api/          # API 라우트
    │   ├── core/         # 설정 및 공통 모듈
    │   ├── models/       # 데이터베이스 모델
    │   ├── schemas/      # Pydantic 스키마
    │   └── services/     # 비즈니스 로직
    ├── tests/            # 테스트 코드
    └── alembic/          # 데이터베이스 마이그레이션
``` 