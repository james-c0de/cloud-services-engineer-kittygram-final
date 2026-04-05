FROM python:3.9

WORKDIR /app

RUN groupadd -g 999 appuser && useradd -u 999 -g appuser -m appuser

COPY requirements.txt .

RUN pip install -r requirements.txt --no-cache-dir

COPY . .

RUN mkdir -p /app/media && chown -R appuser:appuser /app/media

USER appuser

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "kittygram_backend.wsgi"]
