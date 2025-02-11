FROM certbot/certbot

RUN apt-get update && apt-get install -y --no-install-recommends \
    cron && \
    rm -rf /var/lib/apt/lists/*

CMD ["certbot", "certonly", "--webroot", "--webroot-path=/var/www/certbot", "-d", "auth.cxengine.net", "--non-interactive", "--agree-tos", "--email", "your-email@example.com"]
