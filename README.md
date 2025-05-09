# Amor

**Amor** is a demo web page created to practice Docker and Kubernetes. It demonstrates how to containerize and deploy a simple Node.js web application using modern DevOps tools.

## ✨ Features

* A visually appealing landing page with animated hearts and social media icons.
* Dockerized Node.js backend.
* Kubernetes deployment using NodePort service.
* Compatible with local Kind clusters or remote Kubernetes setups.

## 🗂️ Project Structure

| File/Folder    | Description                                |
| -------------- | ------------------------------------------ |
| `app.js`       | Main server script using Express.js        |
| `index.html`   | Front-end HTML page                        |
| `Dockerfile`   | Docker instructions to build the image     |
| `deploy.yaml`  | Kubernetes manifest (Deployment + Service) |
| `package.json` | Node.js dependencies and metadata          |

## ✅ Prerequisites

* Docker installed on your system.
* Kubernetes cluster (e.g., [Kind](https://kind.sigs.k8s.io/) or a cloud provider).
* `kubectl` CLI installed.

---

## 🚀 Getting Started

### 🔹 Option 1: Run with Docker (Locally)

```bash
docker build -t amor .
docker run -p 8081:8081 amor
```

> Open in browser: [http://localhost:8081](http://localhost:8081)

---

### 🔹 Option 2: Deploy to Kubernetes (Using Kind)

1. **Create a Kind cluster with port mapping**:

   ```bash
   curl -s https://raw.githubusercontent.com/ibtisam-iq/SilverKube/main/kind-config-file.yaml | kind create cluster --config -
   ```

2. **Pull the Docker image**:

   ```bash
   docker pull ghcr.io/ibtisam-iq/amor:latest
   ```

3. **Deploy the app to Kubernetes**:

   ```bash
   kubectl apply -f deploy.yaml
   ```

4. **Access the application**:

   * If you used Kind with `extraPortMappings` (e.g., `hostPort: 8081`):
     → [http://localhost:8081](http://localhost:8081)

   * If you're on a remote server and opened port 8081:
     → `http://<Public-IP>:8081`

   * If you expose NodePort `30000` but **did not map it to host**, it may not be reachable externally unless using proper networking settings.

---

## 🧰 Technologies Used

* Node.js
* Express.js
* Docker
* Kubernetes
* Kind (Kubernetes-in-Docker)

---

## 👤 Author

Created by [Muhammad Ibtisam](https://linkedin.com/in/ibtisam-iq) — DevOps learner and open-source enthusiast.
