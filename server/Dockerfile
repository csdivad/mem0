FROM python:3.12-slim

WORKDIR /app

COPY server/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

WORKDIR /app/packages
COPY pyproject.toml README.md LICENSE ./
COPY mem0 ./mem0
RUN pip install --no-cache-dir .

WORKDIR /app
COPY server .

EXPOSE 8000

ENV PYTHONUNBUFFERED=1

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
