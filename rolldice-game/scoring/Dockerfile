FROM python:3.9-slim

RUN apt-get update && apt-get install -y \
    gcc \
    g++ \
    libc-dev \
    libffi-dev \
    libssl-dev \
    make \
    wget

WORKDIR /scoring
COPY requirements.txt .

RUN pip install --upgrade pip setuptools wheel \
    && pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 5001
ENV FLASK_RUN_PORT=5001
ENV FLASK_RUN_HOST=0.0.0.0

CMD ["opentelemetry-instrument", "--service_name", "scorey", "--logs_exporter", "otlp", "flask", "run"]
