# 🎬 ARR Stack with Transmission, Prowlarr, Sonarr, and Radarr

This project sets up a self-hosted media automation environment using Docker Compose with the following components:

- **Transmission**: Torrent downloader
- **Prowlarr**: Indexer manager and proxy
- **Sonarr**: TV series management and automation
- **Radarr**: Movie management and automation

All services are connected via a custom Docker network for ease of access and internal resolution.

---

## 🐳 Docker Services

### 📥 Transmission

- Web UI: [http://localhost:9091](http://localhost:9091)
- Torrent client for downloading

### 🔎 Prowlarr

- Web UI: [http://localhost:9696](http://localhost:9696)
- Handles indexers and connects to Sonarr/Radarr

### 📺 Sonarr

- Web UI: [http://localhost:8989](http://localhost:8989)
- Automates TV shows management

### 🎬 Radarr

- Web UI: [http://localhost:7878](http://localhost:7878)
- Automates movie management

---

## 🧾 Usage

### 1. Clone this repository

```bash
git clone https://github.com/asirkov/servarr-service.git
cd servarr-service
```

### 2. Create `.env` file

Define environment variables used in `docker-compose.yml`:

```dotenv
PUID=1000
PGID=1000
TZ=Europe/Kyiv
USERNAME=your_transmission_user
PASSWORD=your_transmission_password
```

### 3. Run Docker Compose

```bash
docker compose up -d
```

or:

```bash
./start.sh
```

---

## 🌐 Network Configuration

All containers are attached to a custom network `servarrnetwork` with static IPs:

- `transmission`: 172.39.0.2
- `prowlarr`: 172.39.0.3
- `sonarr`: 172.39.0.4
- `radarr`: 172.39.0.5

Subnet: `172.39.0.0/24`

---

## 📁 Volumes

- Configuration and state files are stored in `./<service>` directories.
- Media files are mounted from `/data` — update path accordingly for your system.

---

## ⚠️ Notes

- Make sure ports `9091`, `9696`, `8989`, and `7878` are not occupied.
- If needed, configure reverse proxy or HTTPS externally.

---

## 📄 License

MIT License