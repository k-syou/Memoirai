# Memoirai

회의록이나 회의 텍스트를 업로드하면 요약된 회의 내용과 할일 목록을 자동으로 생성해주는 서비스

## 기술 스택

### 프론트엔드
- React + Vite
- TypeScript
- Tailwind CSS

### 백엔드
- FastAPI
- PostgreSQL
- SQLAlchemy
- Alembic

### 인프라
- Docker
- Docker Compose

## 시작하기

### Docker Compose로 실행 (권장)
```bash
# 전체 서비스 실행
docker compose up -d

# 로그 확인
docker compose logs -f [서비스명]

# 서비스 중지
docker compose down
```

서비스 접근:
- 프론트엔드: http://localhost:3000
- 백엔드 API: http://localhost:8000
- 데이터베이스: localhost:5432

### 로컬에서 직접 실행

#### 프론트엔드 실행
```bash
cd web
npm install
npm run dev
```

#### 백엔드 실행
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
VITE_API_URL=http://localhost:8000
```

### 백엔드 (.env)
```
POSTGRES_SERVER=localhost  # Docker: db
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=memoirai
POSTGRES_PORT=5432
SECRET_KEY=your-secret-key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

## Docker 구성

### 서비스 구성
- web: React 프론트엔드 (Vite 개발 서버)
- server: FastAPI 백엔드
- db: PostgreSQL 데이터베이스

### 볼륨
- postgres_data: 데이터베이스 영속성
- 개발환경 소스코드 마운트 (핫 리로드 지원)

## 프로젝트 구조

```
memoirai/
├── web/                    # 프론트엔드
│   ├── src/
│   │   ├── components/    # 재사용 가능한 컴포넌트
│   │   ├── pages/        # 페이지 컴포넌트
│   │   └── ...
│   ├── public/           # 정적 파일
│   └── Dockerfile        # 프론트엔드 Docker 설정
│
├── server/                # 백엔드
│   ├── app/
│   │   ├── api/          # API 라우트
│   │   ├── core/         # 설정 및 공통 모듈
│   │   ├── models/       # 데이터베이스 모델
│   │   ├── services/     # 비즈니스 로직
│   │   └── ...
│   ├── tests/            # 테스트 코드
│   ├── alembic/          # 데이터베이스 마이그레이션
│   └── Dockerfile        # 백엔드 Docker 설정
│
└── docker-compose.yml    # Docker Compose 설정
``` 