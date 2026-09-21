# Verwende ein schlankes, aktuelles Python-Base-Image
FROM python:3.10-slim-bookworm

# Arbeitsverzeichnis im Container festlegen
WORKDIR /app

# Systemabhängigkeiten für den PostgreSQL-Client (psycopg2) installieren
# DEBIAN_FRONTEND=noninteractive verhindert Abbruch bei interaktiven Zeitzonen-Prompts
RUN apt-get update -y && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    build-essential \
    libpq-dev && \
    rm -rf /var/lib/apt/lists/*

# Zuerst Abhängigkeiten kopieren für optimales Docker Layer-Caching
COPY requirements.txt .

# Python-Paketmanager aktualisieren und Bibliotheken installieren
RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir -r requirements.txt

# Anwendungsquellcode in das Arbeitsverzeichnis kopieren
COPY . .

# Port für die Coworking Analytics API dokumentieren
EXPOSE 5153

# Startbefehl in Exec-Form (JSON-Syntax) zur korrekten Signalweiterleitung
CMD ["python", "app.py"]