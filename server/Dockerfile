FROM python:3.12-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt watchfiles

COPY . .

ENV PYTHONPATH=/app
ENV WATCHFILES_FORCE_POLLING=true
ENV PYTHONDONTWRITEBYTECODE=1

EXPOSE 8000

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000", "--reload", "--reload-dir", "/app", "--reload-include", "*.py"] 