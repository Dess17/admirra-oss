# Admirra OSS

Open-source advertising analytics and synchronization toolkit for agencies and small teams.

Admirra OSS brings data from advertising platforms and analytics systems into one backend/frontend stack. It focuses on practical marketing metrics: spend, impressions, clicks, goals, CPL/CPA, campaign directions, anomaly alerts, scheduled reports, and reusable API integrations.

> This repository is a public OSS snapshot of the Admirra analytics platform core. Production deployments must provide their own API credentials, infrastructure, secrets management, and data protection controls.

## Why this project exists

Marketing teams often use several disconnected systems: Yandex Direct, Yandex Metrika, VK Ads, Avito Ads, spreadsheets, dashboards, and messengers. The same campaign can have spend in one system and conversions in another. Admirra OSS provides a maintainable foundation for:

- collecting advertising metrics from multiple APIs;
- matching campaign spend with conversion goals;
- normalizing CPL/CPA and other performance indicators;
- exposing project dashboards and integration management UI;
- automating synchronization, alerts, and report delivery.

## Features

- Yandex Direct integration for impressions, clicks, spend, campaigns and goals.
- Yandex Metrika integration for counters, goals and conversion analytics.
- VK Ads integration for advertising performance data.
- Avito Ads integration with Yandex Metrika goal matching.
- Project dashboards with spend, CPC, CPL/CPA, leads and dynamics.
- Campaign directions/groups for cross-campaign analytics.
- Anomaly detector foundation for campaign-level alerts.
- Scheduled synchronization workers.
- Telegram/MAX notification and report-linking infrastructure.
- Google Sheets export foundation.
- FastAPI backend with PostgreSQL and SQLAlchemy.
- Vue 3 frontend with Vite.
- Docker Compose local environment.

## Architecture

```text
frontend/ Vue 3 + Vite
        |
        v
backend/ FastAPI API
        |
        +-- PostgreSQL models and migrations
        +-- integrations API
        +-- stats aggregation
        +-- project settings
        +-- reports and notifications
        |
        v
automation/ background synchronization workers
        |
        +-- Yandex Direct
        +-- Yandex Metrika
        +-- VK Ads
        +-- Avito Ads
        +-- Google Sheets
```

## Tech stack

- Python, FastAPI, SQLAlchemy, Alembic
- PostgreSQL
- Vue 3, Vite, Axios
- Docker and Docker Compose
- APScheduler/background workers
- Yandex Direct API, Yandex Metrika API, VK Ads API, Avito Ads API

## Quick start

Requirements:

- Docker
- Docker Compose
- Git

```bash
git clone https://github.com/dess17/admirra-oss.git
cd admirra-oss
cp .env.example .env
docker compose up -d --build
```

Default local services:

- Frontend: `http://localhost:8080`
- Backend API: `http://localhost:8001`
- API docs: `http://localhost:8001/docs`

You must configure your own OAuth applications and API credentials before real synchronization can work.

## Configuration

Copy `.env.example` to `.env` and configure only the providers you need.

Important groups:

- database connection;
- JWT and encryption secrets;
- Yandex OAuth credentials;
- VK Ads credentials;
- Avito Ads credentials;
- Telegram/MAX bots;
- Google service account path;
- SMTP provider;
- AI provider endpoint and API key.

Never commit `.env`, service account JSON files, access tokens, refresh tokens, private keys, or production database dumps.

## Main directories

```text
backend_api/     FastAPI routers and application services
core/            database models, schemas, security and configuration
automation/      background sync workers and platform API clients
ai/              AI report/assistant modules
lead_validator/  lead validation service
admin-panel-vue-main/admin-panel-vue-main/
                 Vue 3 frontend application
alembic/         database migrations
tests/           backend tests and smoke checks
docs/            technical notes and implementation plans
```

## Development

Backend checks:

```bash
python3 -m py_compile core/models.py core/schemas.py backend_api/main.py
```

Frontend build:

```bash
cd admin-panel-vue-main/admin-panel-vue-main
npm install
npm run build
```

Run tests where applicable:

```bash
pytest
```

## Security notes

This repository intentionally does not include:

- production `.env` files;
- service account JSON files;
- OAuth refresh tokens;
- bot tokens;
- server passwords;
- database dumps;
- private deployment history.

If you fork this project, rotate any credentials that were ever used in local development and keep production secrets in a dedicated secret manager.

## Maintainer workflows where Codex helps

This project is a good fit for AI-assisted OSS maintenance because small changes in integration code can break business-critical metrics. Useful Codex workflows include:

- pull request review for API integration changes;
- regression checks for CPL/CPA/spend calculations;
- test generation around synchronization edge cases;
- release notes and migration checklist generation;
- security review for token handling and webhook endpoints;
- documentation updates for new advertising providers.

## Roadmap

- Harden production synchronization with an external queue.
- Add more integration contract tests.
- Improve Avito Ads and Metrika attribution coverage.
- Expand anomaly detector documentation and tests.
- Add reusable dashboards for agency reporting.
- Publish provider-specific setup guides.

## License

License is not final yet. Before external contributions, choose and add a license such as MIT or Apache-2.0.
