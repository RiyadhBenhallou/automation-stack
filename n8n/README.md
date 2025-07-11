# n8n Automation Stack

This folder contains the configuration for running n8n, an extendable workflow automation tool, using Docker Compose. It also includes integration with ngrok for secure public URL exposure.

## Contents
- `docker-compose.yml`: Docker Compose configuration for n8n and ngrok services.
- `local-files/`: Directory for storing files accessible to n8n workflows.

## Services
### n8n
- **Image:** `docker.n8n.io/n8nio/n8n:latest`
- **Ports:** Exposes port `5678` for the n8n web interface.
- **Environment Variables:**
  - `N8N_HOST`: Hostname for n8n (default: `localhost`).
  - `N8N_PORT`: Port for n8n (default: `5678`).
  - `N8N_PROTOCOL`: Protocol used (default: `https`).
  - `WEBHOOK_URL`: Public webhook URL, set using ngrok domain.
  - `GENERIC_TIMEZONE`: Timezone for n8n.
- **Volumes:**
  - `n8n_data`: Persists n8n data.
  - `./local-files:/files`: Mounts local files for workflow access.

### ngrok
- **Image:** `ngrok/ngrok:latest`
- **Purpose:** Exposes n8n to the internet via a secure tunnel.
- **Environment Variables:**
  - `NGROK_AUTHTOKEN`: Your ngrok authentication token.
- **Command:**
  - Exposes port `5678` using the specified static ngrok domain.

## Usage
1. **Configure Environment Variables:**
   - Create a `.env` file in this directory with the following variables:
     ```env
     NGROK_AUTHTOKEN=your_ngrok_authtoken
     NGROK_STATIC_DOMAIN=your-ngrok-domain.ngrok.io
     GENERIC_TIMEZONE=Europe/Paris
     ```
2. **Start the Stack:**
   ```zsh
   docker-compose up -d
   ```
3. **Access n8n:**
   - Local: [https://localhost:5678](https://localhost:5678)
   - Public (via ngrok): `https://${NGROK_STATIC_DOMAIN}`

## Notes
- Ensure your ngrok account supports static domains if using `NGROK_STATIC_DOMAIN`.
- All workflow files can be accessed in the `local-files` directory.
- Data is persisted in the `n8n_data` Docker volume.

## References
- [n8n Documentation](https://docs.n8n.io/)
- [ngrok Documentation](https://ngrok.com/docs)
