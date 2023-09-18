# NAS Services

## Installation

Before starting the Docker Compose stack, you need to create a `user_database.yml` file inside `authelia` folder based on [this model](https://github.com/authelia/authelia/blob/v4.37/examples/compose/lite/authelia/users_database.yml).

### Development

SMTP parameters are optional.

```shell
AUTHELIA_NOTIFIER_SMTP_USERNAME=YOUR_SMTP_USERNAME \
AUTHELIA_NOTIFIER_SMTP_PASSWORD=YOUR_SMTP_PASSWORD \
docker compose up -d
```

### Production

The production environment is ship with Jellyfin MPP to allow hardware transcoding on RK35XX boards.

```shell
DOMAIN=YOUR_DOMAIN \
AUTHELIA_JWT_SECRET=YOUR_JWT_SECRET \
AUTHELIA_SESSION_SECRET=YOUR_SESSION_SECRET \
AUTHELIA_STORAGE_ENCRYPTION_KEY=YOUR_STORAGE_ENCRYPTION_KEY \
AUTHELIA_NOTIFIER_SMTP_USERNAME=YOUR_SMTP_USERNAME \
AUTHELIA_NOTIFIER_SMTP_PASSWORD=YOUR_SMTP_PASSWORD \
JELLYFIN_MEDIA_PATH=YOUR_JELLYFIN_MEDIA_PATH \
DOWNLOADS_PATH=YOUR_DOWNLOADS_PATH \
docker compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```
