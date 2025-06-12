# Memoirai API Server

회의록 자동 요약 및 할일 추출을 위한 FastAPI 기반 백엔드 서버

## 기술 스택

- Python 3.12+
- FastAPI
- PostgreSQL
- SQLAlchemy (ORM)
- Alembic (데이터베이스 마이그레이션)

## 시작하기

1. 의존성 설치
```bash
pip install -r requirements.txt
```

2. 환경 변수 설정
```bash
# .env 파일 생성
cp .env.example .env
# 필요한 환경 변수 설정
```

3. 데이터베이스 설정
```bash
# PostgreSQL 데이터베이스 생성
createdb memoirai

# 마이그레이션 실행
alembic upgrade head
```

4. 개발 서버 실행
```bash
uvicorn app.main:app --reload
```

## API 문서

- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

## 프로젝트 구조

```
server/
├── alembic/            # 데이터베이스 마이그레이션
├── app/
│   ├── api/           # API 라우터
│   ├── core/         # 핵심 설정 및 데이터베이스
│   ├── models/       # SQLAlchemy 모델
│   ├── schemas/      # Pydantic 스키마
│   └── services/     # 비즈니스 로직
├── tests/            # 테스트 코드
├── .env             # 환경 변수
└── requirements.txt  # 의존성 목록
```

## 테스트

```bash
pytest
```

## 라이선스

MIT 