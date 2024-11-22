# Simple HTTP Server Guide

## Overview
Python provides a built-in HTTP server that's perfect for quick file sharing across a network. This lightweight server allows other machines on your network to access files through a web browser.

## Quick Start

### Python 2.x
```bash
# Navigate to the directory you want to share
cd /path/to/share

# Start the server
python -m SimpleHTTPServer
```

### Python 3.x
```bash
# Navigate to the directory you want to share
cd /path/to/share

# Start the server
python3 -m http.server
```

## Accessing Shared Files

### Local Access
```
http://localhost:8000
```

### Remote Access
```
http://IP_ADDRESS:8000
```

## Additional Options

### Specify Custom Port
```bash
# Python 2.x
python -m SimpleHTTPServer 9000

# Python 3.x
python3 -m http.server 9000
```

### Find Your IP Address
```bash
# On Linux/Mac
ifconfig

# On Windows
ipconfig
```

## Best Practices

1. **Security Considerations**
    - Only run the server on trusted networks
    - Don't expose sensitive files
    - Stop the server when not in use (Ctrl+C)

2. **Usage Tips**
    - Ensure the port isn't already in use
    - Check firewall settings if access is blocked
    - Use a custom port if 8000 is unavailable

## Alternative Methods

### Node.js Server
```bash
# Install http-server globally
npm install -g http-server

# Start server
http-server
```

### Python One-Liner for Different Interfaces
```bash
# Bind to specific IP
python3 -m http.server 8000 --bind 192.168.1.100
```

## Common Use Cases

1. **Quick File Sharing**
    - Share files within local network
    - Temporary web hosting
    - Testing static websites

2. **Development**
    - Local development server
    - Testing static content
    - Quick file access

## Troubleshooting

### Common Issues
1. **Port Already in Use**
   ```bash
   # Check if port is in use
   lsof -i :8000
   
   # Use different port
   python3 -m http.server 8080
   ```

2. **Access Denied**
    - Check directory permissions
    - Verify network connectivity
    - Check firewall settings

### Security Notes
- The server exposes all files in the current directory
- No authentication mechanism
- Best suited for temporary sharing on trusted networks

## Quick Reference

```bash
# Basic server (Python 2)
python -m SimpleHTTPServer

# Basic server (Python 3)
python3 -m http.server

# Custom port (Python 3)
python3 -m http.server 9000

# Specific interface binding (Python 3)
python3 -m http.server 8000 --bind 192.168.1.100
```