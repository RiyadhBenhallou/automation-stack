# Automation Stack

This project provides a modular automation stack using Docker Compose, featuring:

- **n8n** for workflow automation
- **ngrok** for secure public URL exposure
- **Flowise** for building and running AI workflows

All services are resource-limited to prevent system overheating and ensure stable operation.

## Structure

- `n8n/`: n8n workflow automation service and configuration
- `flowise/`: Flowise AI workflow service and configuration
- `.gitignore`: Ensures sensitive files like `.env` are not tracked by git
- `docker-compose.yml`: Top-level compose file orchestrating all services

## Features

- **n8n**: Powerful workflow automation with persistent data and file access
- **ngrok**: Securely exposes local services to the internet using static domains and authentication tokens
- **Flowise**: Visual builder for AI-powered workflows
- **Resource Limiting**: All services have CPU and memory limits to avoid overheating
- **Extensible**: Easily add more services or automation tools

## Resource Limits

Each service is configured with sensible CPU and memory limits. You can adjust these in `docker-compose.yml` under the `deploy.resources` section for each service.

## Getting Started

1. **Clone the Repository:**
   ```zsh
   git clone https://github.com/RiyadhBenhallou/automation-stack.git
   cd automation-stack
   ```
2. **Configure Environment Variables:**
   - Create a `.env` file in the root or in each service folder (e.g., `n8n/`) with the required variables. See each service's README for details.
3. **Start All Services:**
   ```zsh
   docker-compose up -d
   ```
4. **Access Services:**
   - **n8n:** [https://localhost:5678](https://localhost:5678) or via your ngrok domain
   - **Flowise:** [http://localhost:3000](http://localhost:3000)
   - **ngrok:** Public URL as configured in your `.env` file

## Security

- Store sensitive environment variables (API keys, tokens, passwords) in `.env` files. These are excluded from version control by `.gitignore`.

## References

- [n8n Documentation](https://docs.n8n.io/)
- [ngrok Documentation](https://ngrok.com/docs)
- [Flowise Documentation](https://docs.flowiseai.com/)

## License

MIT
