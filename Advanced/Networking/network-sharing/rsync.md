# Rsync (Remote Synchronization)

## Overview

Rsync (Remote Synchronization) is an advanced file transfer and synchronization tool that offers significant advantages over simple copy commands. Its key feature is a specialized algorithm that performs differential transfers, copying only the changes between source and destination.

## Key Features

- **Differential Updates**: Only copies changed portions of files
- **Resume Support**: Can continue interrupted transfers
- **Integrity Verification**: Uses checksums to verify file integrity
- **Bandwidth Efficient**: Optimized for network transfers

## Common Use Cases

- Directory synchronization (local and remote)
- Data backups
- Large file transfers
- Server replication
- Website deployment

## Basic Command Options

| Option | Description |
|--------|-------------|
| `-v` | Verbose output |
| `-r` | Recursive into directories |
| `-h` | Human-readable output |
| `-z` | Compression for transfer |

## Command Examples

### Local Synchronization
```bash
# Sync two local directories
rsync -zvr /my/local/directory/one /my/local/directory/two

# Backup with progress
rsync -avh --progress /source/directory /backup/directory
```

### Remote Operations
```bash
# Copy from remote to local
rsync username@remotehost.com:/remote/directory /local/directory

# Copy from local to remote
rsync /local/directory username@remotehost.com:/remote/directory

# Sync entire directory with progress
rsync -avzh --progress /local/dir user@remote:/destination
```

## Advanced Usage

### Additional Useful Options
```bash
# Dry run (no actual changes)
rsync -av --dry-run source/ destination/

# Delete files in destination that aren't in source
rsync -av --delete source/ destination/

# Exclude specific patterns
rsync -av --exclude='*.log' source/ destination/
```

### Backup Creation
```bash
# Create a backup with timestamp
rsync -av --backup --backup-dir=/backup/$(date +%Y-%m-%d) source/ destination/
```

## Best Practices

1. **Testing**
    - Always use `--dry-run` first for important transfers
    - Verify source and destination paths

2. **Performance**
    - Use `-z` compression for slow connections
    - Consider using `-partial` for large files
    - Use `-P` for progress and partial transfer support

3. **Security**
   ```bash
   # Using specific SSH key
   rsync -av -e "ssh -i /path/to/key" source/ user@remote:/destination/
   ```

## Common Patterns

### Mirror Directory Structure
```bash
rsync -av --delete source/ destination/
```

### Incremental Backup
```bash
rsync -av --link-dest=/backup/previous /source/ /backup/current/
```

### Site Deployment
```bash
rsync -avz --delete --exclude='.git' --exclude='node_modules' ./ user@server:/var/www/site/
```

## Troubleshooting

### Common Issues
1. **Permission Denied**
    - Check file permissions
    - Verify SSH keys/authentication
    - Ensure proper sudo/root access

2. **Network Issues**
    - Use `-partial-dir` to handle interruptions
    - Enable compression for slow connections
    - Consider using `--timeout` option

3. **Space Problems**
    - Use `-h` to monitor transfer sizes
    - Check destination disk space
    - Use `--max-size` to limit file sizes

## Tips for Large Transfers

```bash
# Optimized large transfer settings
rsync -avzP --compress-level=9 --stats source/ destination/

# With bandwidth limit
rsync --bwlimit=2000 -avz source/ destination/
```

This guide serves as both a quick reference and a detailed manual for rsync operations. The examples progress from basic to advanced usage, making it suitable for both beginners and experienced users.