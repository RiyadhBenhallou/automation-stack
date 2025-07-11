# Automation Stack

This project provides a modular automation stack using Docker Compose, featuring n8n for workflow automation and ngrok for secure public URL exposure. The stack is organized into separate folders for each service, making it easy to manage and extend.

## Structure
- `n8n/`: Contains the n8n workflow automation service and its Docker Compose configuration.
- `flowise/`: (If present) Contains configuration for Flowise, an AI workflow tool.
- `.gitignore`: Ensures sensitive files like `.env` are not tracked by git.

## Features
- **n8n**: Powerful workflow automation tool with persistent data storage and file access.
- **ngrok**: Securely exposes local services to the internet using static domains and authentication tokens.
- **Extensible**: Easily add more services or automation tools by creating new folders and Docker Compose files.

## Getting Started
1. **Clone the Repository:**
   ```zsh
   git clone https://github.com/RiyadhBenhallou/automation-stack.git
   cd automation-stack
   ```
2. **Configure Environment Variables:**
   - Create a `.env` file in each service folder (e.g., `n8n/`) with the required variables. See the service-specific README for details.
3. **Start Services:**
   - Navigate to the desired service folder and run:
     ```zsh
     docker-compose up -d
     ```
4. **Access Services:**
   - Follow instructions in each service's README to access web interfaces and public URLs.

## Security
- Sensitive environment variables (e.g., API keys, tokens) should be stored in `.env` files, which are excluded from version control by `.gitignore`.

## References
- [n8n Documentation](https://docs.n8n.io/)
- [ngrok Documentation](https://ngrok.com/docs)
- [Flowise Documentation](https://docs.flowiseai.com/) (if applicable)

## License
MIT
