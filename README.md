# Kecloack-IAM
Services for Keycloak, Nginx, and Certbot with volumes and network configurations

#Keycloak with Nginx and Free SSL using Docker

This project sets up Keycloak with Nginx as a reverse proxy and Certbot for SSL certificate generation using Docker Compose.

#Prerequisites

1) Docker & Docker Compose installed
2) A registered domain pointing to your server (e.g., auth.cxengine.net)
3) Ports 80 and 443 open for SSL verification and HTTPS traffic

#Directory Structure
.
├── docker-compose.yml
├── nginx/
│   └── nginx.conf
├── certbot/
│   └── Dockerfile


#Setup Instructions
1) Clone the Repository

2) Configure Keycloak and Nginx
  Edit nginx/nginx.conf to ensure your domain is correctly set:

    server {
      listen 80;
      server_name auth.agcimaging.com;
      
      location /.well-known/acme-challenge/ {
          root /var/www/certbot;
      }
  
      location / {
          return 301 https://$host$request_uri;
      }
  }

3) Build and Start Services
     docker-compose up -d
4) Obtain SSL Certificate
    docker-compose run --rm certbot
5) Restart Services to Apply SSL
    docker-compose restart



#How to Usage
  Access Keycloak via https://auth.agcimaging.com
  Default Admin Credentials:
    Username: admin
    Password: adminpassword

    

#Troubleshooting

  Check Nginx logs                      :  docker logs nginx
  Verify Keycloak container is running  :  docker ps
  Test domain resolution                :  nslookup auth.cxengine.net




