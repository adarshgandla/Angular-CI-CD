# Docker & Auto-Updating Container Setup

### 1. Running the App with Automated Updates (Watchtower)

To run the application alongside **Watchtower** (which checks GHCR for newly pushed images every 60 seconds and auto-updates the running container):

```bash
docker compose up -d
```

- **Application:** Available at `http://localhost:8080`.
- **Auto-Updater:** Watchtower will continuously monitor `ghcr.io/adarshgandla/angular-ci-cd:latest`. When a commit is pushed to `master`, GitHub Actions builds and publishes the new image, and Watchtower automatically pulls it and restarts the container with zero downtime.

### 2. Manual Local Build & Run

If you wish to build the container locally without pulling from GHCR:

```bash
docker compose up -d --build
```

### 3. Viewing Logs

- App logs: `docker logs -f angular-app`
- Auto-update logs: `docker logs -f watchtower`

### 4. Stopping the Services

```bash
docker compose down
```