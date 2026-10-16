# Remote Deployment Guide: Contract Generation System

This guide outlines the steps to deploy and run the containerized Flask Admin UI and FastAPI Documentation Service on a remote host using pre-built Docker images.

---

## 📂 Directory Structure

Ensure your deployment folder on the remote PC is organized as follows:

```text
contract_docker_setup/
├── docker-compose.deploy.yml
├── .env
├── contract_app.tar
├── doc_service.tar
└── app/
    ├── uploaded_templates/        # Shared directory for templates
    └── api_mapper/
        └── template_api_map.json  # Configuration mapping file
```

---

## 🚀 Deployment Steps

### Step 1: Install Docker & Modern Compose Plugin
Ensure Docker and the modern Docker Compose plugin are installed on the remote machine:
```bash
docker --version
docker compose version
```
*(Note: Use `docker compose` with a space, not a hyphen).*

### Step 2: Load the Docker Images
Import the pre-built image archive files into the local Docker daemon. Run these commands from the folder where your `.tar` files are located:
```bash
docker load -i contract_app.tar
docker load -i doc_service.tar
```
*Verify that the images are loaded successfully:*
```bash
docker images
```

### Step 3: Configure Environment Variables
Ensure your `.env` file is placed in the root of the `contract_docker_setup` directory with all required production keys, database strings, and configurations.

### Step 4: Start the Services
Run the following command using your deployment-specific compose file to spin up both containers in detached mode:
```bash
docker compose -f docker-compose.deploy.yml up -d
```

---

## 🔍 Verification & Maintenance

* **Check Container Status:**
  ```bash
  docker compose -f docker-compose.deploy.yml ps
  ```

* **View Service Logs:**
  ```bash
  # View Flask UI logs
  docker logs -f contract_ui_admin

  # View FastAPI service logs
  docker logs -f doc_service_api
  ```

* **Access the Application:**
  * **Flask Admin UI:** `http://<remote-ip>:5001`
  * **FastAPI Docs:** `http://<remote-ip>:8000/docs`

* **Stop Services:**
  ```bash
  docker compose -f docker-compose.deploy.yml down