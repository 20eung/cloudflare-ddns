# Cloudflare DDNS

> Docker Compose를 사용하는 Cloudflare DNS 자동 업데이트 DDNS 설정

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Docker](https://img.shields.io/badge/Docker-Ready-blue.svg)](https://www.docker.com/)
[![Cloudflare](https://img.shields.io/badge/Cloudflare-DDNS-orange.svg)](https://www.cloudflare.com/)

Dynamically updates Cloudflare DNS records to track your public IP address.

## Features

- Automatic IP detection and DNS record updates
- Configurable update interval (default: every 5 minutes)
- IPv4 and IPv6 support
- Docker-based easy deployment

## Prerequisites

- Docker & Docker Compose
- Cloudflare account with a domain

## Quick Start

### 1. Clone and Configure

```bash
git clone https://github.com/yourusername/cloudflare-ddns.git
cd cloudflare-ddns
cp .env.example .env
```

### 2. Set Environment Variables

Edit `.env` file:

```bash
# Cloudflare API Token (create from Cloudflare Dashboard)
CF_API_TOKEN=your_api_token

# Domain(s) to update (comma-separated)
DOMAINS=example.com,sub.example.com

# Zone ID (found in Cloudflare Dashboard)
CF_ZONE_ID=your_zone_id

# Cloudflare Proxy (true/false)
PROXIED=false

# Update interval
UPDATE_CRON=@every 5m

# IP detection provider
IP4_PROVIDER=cloudflare.doh
IP6_PROVIDER=none

DETECTION_TIMEOUT=15s
```

### 3. Run

```bash
docker-compose up -d
```

### 4. Verify

```bash
docker-compose logs -f
```

## Configuration

| Variable | Description | Default |
|----------|-------------|---------|
| `CF_API_TOKEN` | Cloudflare API token | Required |
| `DOMAINS` | Domain(s) to update | Required |
| `CF_ZONE_ID` | Cloudflare Zone ID | Required |
| `PROXIED` | Enable Cloudflare proxy | `false` |
| `UPDATE_CRON` | Update interval | `@every 5m` |
| `IP4_PROVIDER` | IPv4 detection provider | `cloudflare.doh` |
| `IP6_PROVIDER` | IPv6 detection provider | `none` |

## License

MIT License - see [LICENSE](LICENSE) for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.