## docker-strider

docker-compose.yml allows to run full (mongo + mailing) strider setup with one shot.

## Usage

You should have `docker-compose` to be installed first (https://docs.docker.com/compose)

```bash
docker-compose build
docker-compose up -d
```

## Configuration

Update `docker-compose.yml` config according to your settings:

- `postfix.environment.maildomain` to change mail domain
- `strider.environment.SERVER_NAME` to change strider base url
