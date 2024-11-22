# Network File Sharing Overview

## Introduction
Networks typically consist of multiple interconnected computers, especially in commercial environments. While USB drives can be used for data transfer, network file sharing is often more efficient for machines on the same network.

## File Transfer Methods

### Available Options
- Network file sharing protocols
- Directory mounting
- Simple file copies

## SCP (Secure Copy)

### Overview
SCP (Secure Copy) is a command-line utility that allows secure file transfer between hosts on a network. It uses SSH for data transfer and provides the same authentication and encryption as SSH.

### Basic Syntax
```bash
# Copy local file to remote host
scp myfile.txt username@remotehost.com:/remote/directory

# Copy remote file to local host
scp username@remotehost.com:/remote/directory/myfile.txt /local/directory

# Copy entire directory to remote host
scp -r mydir username@remotehost.com:/remote/directory
```

### Common Use Cases

#### 1. Single File Transfer
```bash
# Upload a file
scp document.pdf user@server.com:/home/user/documents/

# Download a file
scp user@server.com:/home/user/documents/report.pdf ./
```

#### 2. Multiple File Transfer
```bash
# Upload multiple files
scp file1.txt file2.txt user@server.com:/destination/

# Download multiple files
scp user@server.com:/remote/path/{file1.txt,file2.txt} ./
```

#### 3. Directory Operations
```bash
# Upload a directory
scp -r local_directory user@server.com:/remote/path/

# Download a directory
scp -r user@server.com:/remote/directory/ local_path/
```

### Advanced Options
```bash
# Preserve file attributes
scp -p myfile.txt user@server.com:/path/

# Use compression
scp -C largefile.zip user@server.com:/path/

# Specify different port
scp -P 2222 file.txt user@server.com:/path/
```

## Best Practices

1. **Security**
    - Always verify the remote host before transfer
    - Use SSH keys instead of passwords when possible
    - Keep your SSH client updated

2. **Performance**
    - Use compression (-C) for large text files
    - Consider alternatives like rsync for large transfers
    - Use wildcard transfers carefully

3. **Organization**
    - Maintain consistent directory structures
    - Use meaningful file names
    - Document shared file locations

## Troubleshooting

Common issues and solutions:
- Permission denied: Check file permissions and ownership
- Connection refused: Verify SSH service is running
- No route to host: Check network connectivity