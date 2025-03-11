# Usa l'immagine base dell'agente Jenkins
FROM jenkins/inbound-agent:latest

# Passa all'utente root per installare le dipendenze
USER root

# Aggiorna i pacchetti e installa Docker
RUN apt-get update && \
    apt-get install -y docker.io

# Installa Python e pip
RUN apt-get install -y python3 python3-pip

# Imposta la directory di lavoro
WORKDIR /app

# Copia il file requirements.txt e installa le dipendenze Python
COPY requirements.txt .
RUN pip3 install -r requirements.txt

# Copia il resto dell'applicazione
COPY . .

# Espone la porta su cui gira l'applicazione (ad esempio, Flask usa la 5000)
EXPOSE 5000

# Imposta il comando di avvio dell'applicazione
CMD ["python3", "-m", "flask", "run", "--host=0.0.0.0"]
