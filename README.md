# Bienenstaat-Apiary Microservices

Dockerized microservices architecture for The Bien Organization's AI-powered infrastructure.

## Architecture

### Bienenstaat
- **Database**: PostgreSQL 16 + pgvector extension
- **Purpose**: Dynasty PDFs, genealogy data, and BEE blocks (Bien Encoded Elements)
- **Features**: Vector embeddings for semantic search, document storage, genealogy relationships

### Apiary.AI
- **Database**: PostgreSQL 16
- **Purpose**: FastAPI workflows for organizational and family automation
- **Features**: Google Calendar/Gmail integration, workflow orchestration, task automation

## Quick Start

```bash
# Clone repository
git clone https://github.com/Phoenix-System-Core/bienenstaat-apiary-microservices.git
cd bienenstaat-apiary-microservices

# Configure environment
cp .env.example .env
# Edit .env with your credentials

# Start all services
docker-compose up -d

# View logs
docker-compose logs -f

# Stop services
docker-compose down
```

## Services

| Service | Port | Description |
|---------|------|-------------|
| bienenstaat-db | 5432 | Postgres + pgvector |
| bienenstaat-api | 8001 | Bienenstaat FastAPI |
| apiary-db | 5433 | Postgres for workflows |
| apiary-api | 8002 | Apiary.AI FastAPI |
| redis | 6379 | Cache & task queue |

## API Endpoints

### Bienenstaat API (http://localhost:8001)
- `GET /health` - Health check
- `POST /dynasty/upload` - Upload dynasty PDF
- `POST /dynasty/search` - Vector search PDFs
- `GET /bee-blocks` - List BEE blocks
- `POST /bee-blocks` - Create BEE block

### Apiary.AI API (http://localhost:8002)
- `GET /health` - Health check
- `GET /workflows` - List workflows
- `POST /workflows/trigger` - Trigger workflow
- `GET /calendar/events` - Fetch calendar events
- `POST /email/send` - Send email via Gmail

## Development

```bash
# Rebuild specific service
docker-compose up -d --build bienenstaat-api

# Access database
docker exec -it bienenstaat-db psql -U bienenstaat -d bienenstaat

# View service logs
docker-compose logs -f apiary-api
```

## License

Proprietary - The Bien Organization
