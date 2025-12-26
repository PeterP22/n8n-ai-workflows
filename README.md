# n8n AI Workflows

A curated collection of n8n automation workflows for AI-powered tasks. All workflows are designed for local/self-hosted deployment with minimal or zero API costs.

## Workflows

| Workflow | Description | Stack | Docs |
|----------|-------------|-------|------|
| **SeedDream Image Generator** | Generate AI images via Replicate API, delivered to Telegram | Replicate, Telegram | [README](seedream-image-generator/README.md) |
| **AI Research Digest** | Daily aggregation of AI/ML news from arXiv, HN, HuggingFace, Reddit | Ollama, Telegram | [README](ai-research-digest/README.md) |

## Tech Stack

| Component | Service | Notes |
|-----------|---------|-------|
| Workflow Engine | [n8n](https://n8n.io/) | Self-hosted automation |
| Local LLM | [Ollama](https://ollama.ai/) | llama3.2, mxbai-embed-large |
| Vector Store | [Qdrant](https://qdrant.tech/) | Local embeddings storage |
| Notifications | Telegram | Bot API delivery |
| Image Gen | [Replicate](https://replicate.com/) | SeedDream 4.5, FLUX, etc. |

## Quick Start

### Prerequisites

- Docker with [self-hosted-ai-starter-kit](https://github.com/n8n-io/self-hosted-ai-starter-kit)
- n8n running on port 5678
- Ollama for local LLM inference

### Start the Stack

```bash
cd /path/to/self-hosted-ai-starter-kit
docker compose --profile cpu up -d

# Access n8n
open http://localhost:5678
```

### Import a Workflow

1. Open n8n at `http://localhost:5678`
2. Go to **Workflows** → **Import from File**
3. Select `workflow.json` from any workflow folder
4. Configure credentials as needed (see workflow's README)

## Repository Structure

```
.
├── README.md                        # This file (index)
├── seedream-image-generator/
│   ├── README.md                    # SeedDream docs
│   ├── workflow.json                # n8n workflow
│   └── workflow.png                 # Workflow diagram
└── ai-research-digest/
    ├── README.md                    # AI Digest docs
    ├── workflow.json                # n8n workflow
    └── workflow.png                 # Workflow diagram
```

## Adding New Workflows

1. Create folder: `{workflow-name}/`
2. Export workflow JSON from n8n → `{workflow-name}/workflow.json`
3. Create `{workflow-name}/README.md` with documentation
4. Add workflow diagram → `{workflow-name}/workflow.png`
5. Add entry to the Workflows table above

## Philosophy

- **Local-first** - Prefer self-hosted solutions (Ollama, Qdrant) over paid APIs
- **Zero/low cost** - Minimize recurring API expenses
- **Telegram delivery** - Universal notification target
- **Modular** - Each workflow is independent and well-documented

---

*Built with n8n + Ollama + Docker*
