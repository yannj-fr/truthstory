# TruthStory

TruthStory is a SaaS platform for comprehensive media and news analysis, leveraging web crawling, AI, and knowledge graphs to analyze news content authenticity and propagation patterns.

## Quick Start

1. Clone and setup:
```bash
git clone https://github.com/yannj-fr/truthstory.git
cd truthstory
pip install -r requirements.txt
cd ui && npm install
```

2. Start services:
```bash
docker-compose up -d
```

## Development

- Development ports: 53028 (primary), 57585 (secondary)
- Server config: CORS and iframes enabled, accessible via 0.0.0.0

For detailed documentation, see:
- [Architecture Overview](specifications/architecture/overview.yaml)
- [Development Guidelines](specifications/development.yaml)
- [Service Specifications](specifications/services/)
- [Interface Specifications](specifications/interfaces/)
- [Data Models](specifications/data-models/)

## License

MIT License - see LICENSE file for details.