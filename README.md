## 👋 Welcome to paperless-ngx 🚀

Document management system with OCR and full-text search

## 📋 Description

Document management system with OCR and full-text search

## 🚀 Services

- **paperless-ngx**: ghcr.io/paperless-ngx/paperless-ngx:latest

### Infrastructure Components

- **paperless-ngx-db**: Postgres database
- **paperless-ngx-redis**: Redis database


## 📦 Installation

### Option 1: Quick Install
```bash
curl -q -LSsf "https://raw.githubusercontent.com/composemgr/paperless-ngx/main/docker-compose.yaml" -o compose.yml
```

### Option 2: Git Clone
```bash
git clone "https://github.com/composemgr/paperless-ngx" ~/.local/srv/docker/paperless-ngx
cd ~/.local/srv/docker/paperless-ngx
docker compose up -d
```

### Option 3: Using composemgr
```bash
composemgr install paperless-ngx
```

## 🔧 Configuration

### Environment Variables

```shell
TZ=America/New_York
DB_CREATE_DATABASE_NAME=paperless
DB_USER_NAME=paperless
DB_USER_PASS=changeme_db_password
APP_SECRET_KEY=changeme_secret_key
APP_ADMIN_USER=admin
APP_ADMIN_PASS=changeme_admin_password
APP_ADMIN_USER=admin
TZ=America/New_York
EMAIL_SERVER_HOST=172.17.0.1
# ... see docker-compose.yaml for more
```

See `docker-compose.yaml` for complete list of configurable options.

## 🌐 Access

- **Web Interface**: http://172.17.0.1:8000

## 📂 Volumes

- `./volumes/data/paperless-ngx` - Data storage
- `./volumes/data/media/documents` - Data storage
- `./volumes/data/export` - Data storage
- `./volumes/data/consume` - Data storage
- `./volumes/data/db/postgres/paperless-ngx` - Data storage

## 🔐 Security

- Change all default passwords before deploying to production
- Use strong secrets for all authentication tokens
- Configure HTTPS using a reverse proxy (nginx, traefik, caddy)
- Regularly update Docker images for security patches
- Backup your data regularly

## 🔍 Logging

```shell
docker compose logs -f paperless-ngx
```

## 🛠️ Management

```bash
# Start services
docker compose up -d

# Stop services
docker compose down

# Update to latest images
docker compose pull && docker compose up -d

# View logs
docker compose logs -f

# Restart services
docker compose restart
```

## 📋 Requirements

- Docker Engine 20.10+
- Docker Compose V2+

## 🤝 Author

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🦄 composemgr: [Github](https://github.com/composemgr) 🦄
