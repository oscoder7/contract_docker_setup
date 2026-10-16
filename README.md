# Enterprise Contract Generation System

A containerized, decoupled enterprise solution for generating dynamic documents and managing templates securely across environments.

---

## 🏗️ Architecture Overview

The system is split into two independent services communicating over a secure Docker internal network:

1. **Admin UI (`contract_ui_admin`)**: Handles user authentication, role-based access control, template CRUD operations, and administrative workflows.
2. **Document Service (`doc_service_api`)**: Handles high-performance document generation processing using MS Word and API configuration mappings.

---

## 🚀 Quick Start (Local Development)

1. Clone the repository and navigate to your setup folder.
2. Ensure your `.env` file is properly configured with your keys and secrets.
3. Build and launch the containers locally using Docker Compose:
   ```bash
   docker compose up --build -d
   ```
4. Access the applications:
   * **Admin UI**: `http://localhost:5001`
   * **Doc Services**: `http://localhost:8000/docs`

---
5. Login with admin/admin123
## 📦 Remote Deployment

For deploying pre-built images to a remote test environment, please refer to the [Remote Deployment Guide](remote_deployment_guide.md) for step-by-step instructions.