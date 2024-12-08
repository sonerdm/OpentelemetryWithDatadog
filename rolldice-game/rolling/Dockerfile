FROM python:3.9-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc \
    g++ \
    libc-dev \
    libffi-dev \
    libssl-dev \
    make \
    bash \
    wget \
    curl \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /rolling

COPY requirements.txt .

RUN pip install --upgrade pip setuptools wheel \
    && pip install -r requirements.txt --no-cache-dir

COPY . .

EXPOSE 5004

ENV FLASK_RUN_PORT=5004
ENV FLASK_RUN_HOST=0.0.0.0

CMD ["opentelemetry-instrument", "--service_name", "dicey", "--logs_exporter", "otlp", "flask", "run"]
