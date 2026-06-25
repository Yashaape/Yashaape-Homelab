# CasaOs

**Purpose:**
An open source solution to provide a personal cloud service for users to manage and monitor self-hosted applications.

Deployment:
runs the bash script curl -fsSL https://get.casaos.io | sudo bash to install on a linux system.

**Benefits:**

- Simplifies Docker container management through a user-friendly UI
- Centralized dashboard for managing self-hosted services
- Lowers the barrier to entry for Linux and container management
- Enables quick deployment of applications without manual CLI configuration
- Provides visibility into system resources (CPU, RAM, storage usage)
- Supports a modular app-based ecosystem for expanding homelab services

**Integration:**

- Acts as the primary management layer for the homelab server
- Used to deploy and manage services such as Vaultwarden, Jellyfin, and Nginx Proxy Manager
- Works alongside Ubuntu Server as the underlying operating system
- Provides the interface for Docker container orchestration in the environment
- Supports services exposed through Nginx Proxy Manager and secured via DuckDNS

**Lessons Learned:**

- Introduction to container-based application management
- Understanding of Docker abstraction through a GUI layer
- Importance of balancing simplicity (UI tools) with deeper CLI knowledge
- Learned how application platforms abstract system-level configuration
- Gained experience managing multiple services in a centralized interface
- Reinforced concepts of system resource monitoring and service lifecycle management
---

# Vaultwarden

**Purpose:**
Password management solution.

**Deployment:**
Docker container managed through CasaOS.

**Benefits:**
- Self-hosted credential storage and personal management of password data
- Browser integration with bitwarden
- Mobile application support

**Lessons Learned:**
- Container management
- Secure credential handling
- Backup considerations
---

# Nginx Proxy Manager 

**Purpose:**
Reverse proxy and SSL management tool used to expose and manage internal services securely.

**Deployment:**
Deployed as a Docker container through CasaOS.

Configured to manage external access to internal services, including Vaultwarden, using DuckDNS for dynamic DNS resolution.

**Benefits:**
- Simplified reverse proxy configuration via web UI
- Easy SSL certificate management (Let’s Encrypt)
- Centralized control of service routing
- Enables secure external access to homelab services without manual Nginx configuration
- Works with dynamic DNS (DuckDNS) for home IP environments

**Integration:**
- Used DuckDNS to provide a stable domain pointing to a dynamic residential IP
- Routed external traffic to internal services (e.g., Vaultwarden)
- Provided HTTPS termination and secure access layer in front of homelab services

**Lessons Learned:**
- Reverse proxy concepts (routing, upstream services, ports)
- DNS fundamentals and dynamic DNS behavior
- SSL/TLS certificate setup and automation
- Importance of not exposing internal services directly to the internet
- Practical exposure to real-world web service architecture
---

# Portainer

**Purpose:**  
A container management platform that provides a web-based UI for managing Docker environments.

**Deployment:**  
Deployed as a Docker container, typically running on the same host as other self-hosted services. It connects to the local Docker socket to manage containers, images, networks, and volumes.

**Benefits:**

- Simplifies Docker container management through a graphical interface
- Provides visibility into running containers and system resources
- Enables easy deployment, stopping, and updating of containers
- Reduces reliance on CLI for routine container operations

**Integration:**

- Manages Docker containers across the homelab environment
- Works alongside services deployed via CasaOS or manually via Docker
- Can monitor and control services like Jellyfin, Vaultwarden, and Nginx Proxy Manager

**Lessons Learned:**

- Understanding Docker architecture and container lifecycle
- Importance of monitoring and managing containerized services
- Exposure to networking between containers and host systems
- Practical experience with infrastructure visualization and control
---

# Pi-hole

**Purpose:**  
A network-wide DNS filtering system used to block ads, trackers, and malicious domains.

**Deployment:**  
Installed on a local Linux server (often via Docker or native install), configured as the primary DNS server for the home network.

**Benefits:**

- Blocks ads and tracking domains across all devices on the network
- Improves network privacy and security
- Reduces bandwidth usage
- Provides DNS-level visibility into network traffic

**Integration:**

- Set as the primary DNS server for home network devices
- Works alongside router DHCP settings or static DNS configuration
- Can integrate with DHCP services for full network control
- Complements VPN solutions like Tailscale for secure remote access

**Lessons Learned:**

- DNS fundamentals and how domain resolution works
- Network-level filtering and traffic control
- Importance of privacy and threat mitigation at the DNS layer
- Troubleshooting network connectivity and DNS misconfigurations
---

# Uptime Kuma

**Purpose:**  
A self-hosted monitoring tool used to track service uptime, availability, and performance.

**Deployment:**  
Deployed as a Docker container and accessed via a web interface to configure monitors for services and endpoints.

**Benefits:**

- Real-time monitoring of homelab services
- Alerts for downtime via notifications (email, webhook, etc.)
- Simple and intuitive dashboard for system health tracking
- Supports HTTP, TCP, ICMP, and other monitoring types

**Integration:**

- Monitors services such as Jellyfin, Vaultwarden, and Nginx Proxy Manager
- Runs alongside other Docker-based services in the homelab
- Can integrate with notification systems for alerts on service failure

**Lessons Learned:**

- Importance of observability in infrastructure management
- Basics of service health monitoring and alerting
- Understanding uptime vs. availability concepts
- Exposure to proactive system maintenance practices
---

# Jellyfin

**Purpose:**  
A self-hosted media server used for streaming movies, TV shows, and music across devices.

**Deployment:**  
Installed as a Docker container or via CasaOS on Ubuntu Server, with media stored on local NAS drives and mounted into the container.

**Benefits:**

- Free and open-source alternative to commercial streaming platforms
- Full control over media library and access permissions
- Supports streaming to multiple devices (TV, mobile, web)
- No subscription or external dependency required

**Integration:**

- Connected to NAS storage for media files
- Accessed remotely via Tailscale-secured network
- Can be routed through Nginx Proxy Manager with DuckDNS for external access
- Managed alongside other Docker-based services in CasaOS or Portainer

**Lessons Learned:**

- Media server architecture and transcoding concepts
- Storage management and file organization best practices
- Network streaming and bandwidth considerations
- User access control and service exposure security
- Practical experience with self-hosted entertainment infrastructure
