# 🎬 SeedBox Lite

Stream Torrents Instantly

> [!NOTE]
> The [original SeedBox project](https://github.com/hotheadhacker/seedbox-lite) was buggy and misconfigured, here is a cleaned up version, made to work on Docker

<div align="center">

![SeedBox Lite](https://img.shields.io/badge/SeedBox-Lite-green?style=for-the-badge&logo=leaf)
![Docker](https://img.shields.io/badge/Docker-Enabled-blue?style=for-the-badge&logo=docker)
![React](https://img.shields.io/badge/React-19.1.1-61dafb?style=for-the-badge&logo=react)
![Node.js](https://img.shields.io/badge/Node.js-18+-green?style=for-the-badge&logo=node.js)

**A modern, lightweight torrent streaming application with instant playback**

<img src="https://raw.githubusercontent.com/hotheadhacker/seedbox-lite/refs/heads/main/screenshots/details-screen.png" alt="SeedBox Lite Screenshot" width="80%"/>

[View all screenshots](https://github.com/hotheadhacker/seedbox-lite/tree/main/screenshots)

[Features](#-features) • [Screenshots](#-screenshots) • [Quick Start](#-quick-start) • [Installation](#-installation) • [Documentation](#-documentation)

</div>

## 🚀 Overview

SeedBox Lite is a cutting-edge torrent streaming platform that allows you to watch movies and TV shows instantly without waiting for complete downloads. Built with modern web technologies, it provides a Netflix-like experience with powerful torrent capabilities.

### ✨ Key Highlights

- **🎯 Instant Streaming** - Start watching immediately as the torrent downloads
- **🔐 Password Protection** - Secure access with authentication
- **📱 Mobile Optimized** - Perfect responsive design for all devices
- **🎥 Smart Video Player** - Advanced player with subtitles and fullscreen support
- **⚡ Fast Setup** - Deploy in minutes with Docker or PM2
- **🌐 Cross-Platform** - Works on Windows, macOS, and Linux
- **🎨 Modern UI** - Clean, intuitive interface inspired by popular streaming services

## 🎯 Features

### Core Streaming Features

- **Torrent to Stream** - Convert any movie/TV torrent to instant streaming
- **Progress Tracking** - Real-time download progress and cache management
- **Smart Caching** - Intelligent caching system with configurable limits
- **Multiple Formats** - Support for MP4, MKV, AVI, and more video formats
- **Subtitle Support** - Automatic subtitle detection and loading

### User Experience

- **Netflix-Style Interface** - Familiar and intuitive design
- **Mobile-First Design** - Optimized for smartphones and tablets
- **Native Fullscreen** - True fullscreen experience on mobile devices
- **Gesture Controls** - Double-tap to fullscreen, intuitive video controls
- **Responsive Layout** - Adapts perfectly to any screen size

### Technical Features

- **Password Authentication** - Secure access control
- **CORS Enabled** - Cross-origin resource sharing for flexible deployment
- **Health Monitoring** - Built-in health checks and monitoring
- **Production Ready** - Optimized for production deployments
- **Docker Support** - Easy containerized deployment
- **PM2 Integration** - Process management for Node.js applications

### Mobile Optimizations

- **iOS Safari Support** - Native fullscreen using WebKit APIs
- **Android Chrome** - Optimized for Android mobile browsers
- **Range Requests** - HTTP range support for smooth video seeking
- **Mobile Viewport** - Proper viewport handling for app-like experience
- **Touch Optimized** - Gesture-friendly video controls

## 📸 Screenshots

[View all screenshots](https://github.com/hotheadhacker/seedbox-lite/tree/main/screenshots)

## 🚀 Quick Start

### Using Docker

```bash
# Clone the repository
git clone https://github.com/hotheadhacker/seedbox-lite.git
cd seedbox-lite

# Start with Docker Compose
docker-compose up -d

# Access the application
open http://localhost:5174
```

## 📋 Prerequisites

### System Requirements

- **Docker** 20+

### Operating System Support

- ✅ Windows 10/11
- ✅ macOS 10.15+
- ✅ Ubuntu 18.04+
- ✅ Debian 10+
- ✅ CentOS 7+

### Browser Support

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+
- ✅ Mobile browsers (iOS Safari, Android Chrome)

## 🛠 Installation

### TL;DR

Here is the quick installation guide using Docker:

```bash
git clone https://github.com/iu2frl/seedbox-lite.git
cd seedbox-lite
cp .env.sample .env
# Edit .env to configure settings
nano .env
docker-compose up -d
```

### Full Docker Deployment

#### Step 1: Clone Repository

```bash
git clone https://github.com/iu2frl/seedbox-lite.git
cd seedbox-lite
```

#### Step 2: Configure Environment

See below for environment variable configuration. You can edit the `.env` file to customize settings.

```bash
# Copy and edit environment variables
nano .env
```

**Key Environment Variables:**

```env
# Change these to match your server configuration
SERVER_ADDRESS=192.168.0.254
API_PORT=3001
ACCESS_PASSWORD=seedbox123

# Change these only if you know what you're doing
SERVER_HOST=0.0.0.0
SERVER_PROTOCOL=http
VITE_API_BASE_URL=http://localhost:3001
FRONTEND_URL=http://localhost:5174
OPENSUBTITLES_API_URL=https://rest.opensubtitles.org
SUBTITLE_SEEKER_API_URL=https://api.subtitleseeker.com
NODE_ENV=development
WEBTORRENT_ENABLE_UTP=true
```

#### Step 3: Deploy

```bash
# Start all services
docker-compose up -d

# Check status
docker-compose ps

# View logs
docker-compose logs -f
```

#### Step 4: Access Application

- **Frontend**: http://localhost:5174
- **Backend API**: http://localhost:3001/api/health
- **Default Login**: Password set in `ACCESS_PASSWORD`

## 🧪 Testing

### Docker Testing

```bash
# Health check
curl http://localhost:3001/api/health
curl http://localhost:5174/health

# API endpoints
curl -X POST http://localhost:3001/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"password":"your_password"}'

# Cache stats
curl http://localhost:3001/api/cache/stats
```

## 📚 Configuration

### Environment Variables Reference

#### Backend Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `NODE_ENV` | `production` | Application environment |
| `API_PORT` | `3001` | Backend API server port |
| `SERVER_HOST` | `0.0.0.0` | Backend server host |
| `ACCESS_PASSWORD` | `seedbox123` | Authentication password |
| `MAX_CACHE_SIZE` | `5GB` | Maximum cache size |
| `CLEANUP_INTERVAL` | `1h` | Cache cleanup interval |

#### Frontend Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `VITE_API_BASE_URL` | `http://localhost:3001` | Backend API URL |
| `FRONTEND_URL` | `http://localhost:5174` | Frontend URL |

#### Docker Variables

| Variable | Default | Description |
|----------|---------|-------------|
| `API_PORT` | `3001` | Docker backend port mapping |
| `FRONTEND_PORT` | `5174` | Docker frontend port mapping |

### Advanced Configuration

#### Nginx Configuration (Production)

```nginx
server {
    listen 80;
    server_name your-domain.com;
    
    location / {
        proxy_pass http://localhost:5174;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
    
    location /api/ {
        proxy_pass http://localhost:3001;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

#### SSL/HTTPS Setup

```bash
# Install Certbot
sudo apt install certbot python3-certbot-nginx

# Get SSL certificate
sudo certbot --nginx -d your-domain.com

# Auto-renewal
sudo crontab -e
# Add: 0 12 * * * /usr/bin/certbot renew --quiet
```

## 🔧 Troubleshooting

### Common Issues

#### Port Conflicts

```bash
# Check if ports are in use
lsof -i :3001
lsof -i :5174

# Kill processes using ports
sudo kill -9 $(lsof -ti:3001)
sudo kill -9 $(lsof -ti:5174)
```

#### Docker Issues

```bash
# Rebuild containers
docker-compose down
docker-compose up --build

# Clear Docker cache
docker system prune -a

# Check container logs
docker-compose logs seedbox-backend
docker-compose logs seedbox-frontend
```

#### Permission Issues

```bash
# Fix file permissions
sudo chown -R $USER:$USER .
chmod +x deploy.sh

# Docker permission issues
sudo usermod -aG docker $USER
newgrp docker
```

#### Mobile Video Issues

- Ensure CORS is enabled in backend
- Check video format compatibility
- Verify range request support
- Test with different browsers

## 📖 API Documentation

### Authentication Endpoints

```bash
POST /api/auth/login
{
  "password": "your_password"
}
```

### Torrent Endpoints

```bash
GET /api/torrents/search?q=movie+name
POST /api/torrents/add
{
  "magnetLink": "magnet:..."
}
```

### Streaming Endpoints

```bash
GET /api/stream/:torrentId/:fileIndex
Range requests supported for video seeking
```

### Cache Management

```bash
GET /api/cache/stats
POST /api/cache/clear
```

## 🛡 Security

### Best Practices

- Change default password immediately
- Use HTTPS in production
- Keep dependencies updated
- Enable firewall rules
- Regular security audits

### Security Headers

The application includes security headers:
- X-Frame-Options: SAMEORIGIN
- X-Content-Type-Options: nosniff
- X-XSS-Protection: 1; mode=block
- Referrer-Policy: no-referrer-when-downgrade

## 🚀 Deployment

### Production Deployment Checklist

- [ ] Change default passwords
- [ ] Configure HTTPS/SSL
- [ ] Set up monitoring
- [ ] Configure backups
- [ ] Set up log rotation
- [ ] Configure firewall
- [ ] Test mobile compatibility
- [ ] Verify video streaming
- [ ] Test authentication
- [ ] Monitor performance

### Scaling

For high-traffic deployments:
- Use load balancer (nginx/HAProxy)
- Scale backend horizontally
- Implement Redis for session storage
- Use CDN for static assets
- Monitor resource usage

## 📞 Support

### Getting Help

- 📖 [Documentation](./docs/)
- 🐛 [Issue Tracker](https://github.com/hotheadhacker/seedbox-lite/issues)
- 💬 [Discussions](https://github.com/hotheadhacker/seedbox-lite/discussions)

### Contributing

1. Fork the repository
2. Create feature branch
3. Make changes
4. Add tests
5. Submit pull request

## ⚠️ Legal Disclaimer

**IMPORTANT: Please read this disclaimer carefully before using SeedBox Lite.**

SeedBox Lite is an open-source project provided for educational and personal use only. We do not endorse, promote, or facilitate copyright infringement, illegal streaming, or piracy in any form. This software is designed to be used with legal content only.

- We do not host, store, or distribute any content. All torrents and media are accessed through your own connections.
- This application is intended for use with content that you have the legal right to access and stream.
- Users are solely responsible for how they use this software and for ensuring compliance with all applicable laws in their jurisdiction.
- The creators and contributors of SeedBox Lite take no responsibility for how this software is used.
- Using torrents to download or share copyrighted materials without permission may be illegal in your country.

By using SeedBox Lite, you acknowledge that you understand these terms and agree to use the software responsibly and legally.

## 📄 License

This project is licensed under the **Custom Non-Commercial License** - see the [LICENSE](LICENSE) file for details.

**Important License Restrictions:**

- This software is provided for personal, educational, and non-commercial use only
- Commercial use is strictly prohibited without explicit written permission
- Redistribution must include this license and copyright notice
- No warranty or liability is provided with this software

## 🙏 Acknowledgments

- WebTorrent for torrent streaming capabilities
- React team for the amazing framework
- Docker community for containerization
- All contributors and users

---

<div align="center">

**Made with ❤️ by [iu2frl](https://github.com/iu2frl)**

⭐ Star this repo if you find it useful!

</div>
