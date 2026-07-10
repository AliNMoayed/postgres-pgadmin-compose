# PostgreSQL + pgAdmin with Docker Compose

A simple Docker Compose setup for running PostgreSQL and pgAdmin together for local development and database management.

## Features

- PostgreSQL container with persistent storage.
- pgAdmin web interface for browser-based database administration.
- Shared Docker network for service communication.
- Easy startup with a single Docker Compose command.

## Requirements

- Docker
- Docker Compose

## Services

### PostgreSQL
- Image: `docker.arvancloud.ir/postgres`
- Container: `postgres`
- Default user: `postgres`
- Default password: `AliMoayed`

### pgAdmin
- Image: `dpage/pgadmin4:snapshot`
- Container: `pgadmin`
- Login email: `admin@gmail.com`
- Login password: `admin`
- Web UI: `http://localhost:8080`

## Usage

### Start the stack

```bash
docker compose up -d
```

### Stop the stack

```bash
docker compose down
```

### Remove containers and volumes

```bash
docker compose down -v
```

## pgAdmin Connection Settings

After logging into pgAdmin, create a new server connection with the following values:

- Host name/address: `postgres`
- Port: `5432`
- Maintenance database: `postgres`
- Username: `postgres`
- Password: `AliMoayed`

Because both services are attached to the same Docker network, pgAdmin can reach PostgreSQL using the service name `postgres`.

## Persistence

This setup uses Docker volumes to keep data after container restarts:

- `postgres_data` stores PostgreSQL data.
- `pgadmin_data` stores pgAdmin configuration and saved connections.

## Notes

- `depends_on` controls startup order, but it does not wait for PostgreSQL to become fully ready.
- For production use, consider moving passwords to an `.env` file or Docker secrets.
- The `snapshot` tag for pgAdmin is suitable for testing and local development.

## Repository Structure

```text
.
├── docker-compose.yml
└── README.md
```

## License

MIT
