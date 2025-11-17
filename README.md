# 🛡️ PrivNet — Secure Self-Hosted Privacy Network Stack

**WireGuard + Pi-hole + Unbound + Shadowsocks — Fully Automated Setup**

PrivNet is an all-in-one, self-hosted privacy network solution that deploys:

-   **WireGuard VPN**
-   **Pi-hole** (DNS-level ad blocker & tracker filter)
-   **Unbound** recursive DNS resolver
-   **Shadowsocks** proxy
-   **Docker-based** orchestration

All components are deployed automatically using a single shell script (`setup.sh`) and a Docker Compose stack.

This project is designed for users who want a private, censorship-resistant, and tracker-free network environment.

---

## 🚀 Features

-   **🔐 WireGuard VPN**
    -   A high-performance, modern VPN for secure remote access.
-   **🚫 Pi-hole**
    -   Network-level ad and tracker blocking for all connected devices.
-   **🌀 Unbound**
    -   A local DNS resolver for encrypted, private DNS lookups without third parties.
-   **🕶️ Shadowsocks**
    -   A fast proxy for bypassing censorship and improving privacy.
-   **🐳 Dockerized**
    -   All services run in isolated containers for stability and easy updates.

---

## 📦 What the Setup Script Does

The `setup.sh` script performs:

1.  **System Update**
    ```bash
    sudo apt-get update -y && sudo apt-get upgrade -y
    ```
2.  **Installs Dependencies**
    -   `curl`
    -   `git`
    -   `ca-certificates`
    -   `apt-transport-https`
    -   `software-properties-common`
3.  **Installs Docker & Docker Compose v2**
    -   Adds Docker GPG keys, repositories, and installs:
        -   `docker-ce`
        -   `docker-ce-cli`
        -   `containerd.io`
        -   `docker-compose-plugin`
4.  **Clones This Repository**
    ```bash
    git clone https://github.com/QuantTitan/PrivNet.git
    ```
5.  **Starts All Services**
    ```bash
    sudo docker compose up -d
    ```

---

## 🛠️ Installation

1️⃣ **Download and run the setup script**
```bash
curl -O https://raw.githubusercontent.com/QuantTitan/PrivNet/master/setup.sh
chmod +x setup.sh
sudo ./setup.sh
```

---

## 📁 Repository Structure

```
PrivNet/
├── docker-compose.yml   # Main stack
├── config/              # Additional configs (if any)
├── setup.sh             # Installer script
└── README.md
```

---

## ▶️ Managing the Services

**Start**
```bash
sudo docker compose up -d
```

**Stop**```bash
sudo docker compose down
```

**View logs**
```bash
sudo docker compose logs -f
```

---

## 🔍 Verifying the Setup

**Check Docker versions:**
```bash
docker --version
docker compose version
```

**Check running containers:**
```bash
docker ps
```
You should see containers for:
-   WireGuard
-   Pi-hole
-   Unbound
-   Shadowsocks

---

## 🌐 Accessing Services

| Service             | Default Location                             |
|---------------------|----------------------------------------------|
| Pi-hole Admin Panel | `http://<server-ip>/admin`                     |
| WireGuard Configs   | Stored in container volume or generated via UI |
| Shadowsocks         | As defined in `docker-compose`                 |
| Unbound DNS         | Used automatically by Pi-hole                |

---

## 🔒 Security Notes

-   Always change default passwords.
-   Restrict SSH access to your server.
-   Keep Docker images updated.

---

## 🤝 Contributing

Pull requests are welcome!
Feel free to submit improvements, enhancements, or bug fixes.

---

## 📜 License

MIT License — free to use, modify, and distribute.
