# Database Connection Configuration

This document explains how to configure database connections for the MSSQL MCP Server.

## Command-Line Arguments

You can specify database connection parameters directly via command-line arguments:

```bash
# Basic usage
node server.mjs --host your-server.database.windows.net --database your_db --username your_user --password your_password

# Alternative parameter names
node server.mjs --server your-server.database.windows.net --database your_db --user your_user --password your_password

# With port specification
node server.mjs --host your-server.database.windows.net --port 1433 --database your_db --username your_user --password your_password
```

## Supported Parameters

| Parameter | Alternative | Description |
|-----------|-------------|-------------|
| `--host` | `--server` | Database server hostname |
| `--database` | - | Database name |
| `--username` | `--user` | Database username |
| `--password` | - | Database password |
| `--port` | - | Database port (default: 1433) |

## Environment Variables

You can also use environment variables for configuration:

- `DB_SERVER`: Database server hostname
- `DB_DATABASE`: Database name
- `DB_USER`: Database username
- `DB_PASSWORD`: Database password
- `DB_PORT`: Database port
- `DB_ENCRYPT`: Enable encryption ('true'/'false')
- `DB_TRUST_SERVER_CERT`: Trust server certificate ('true'/'false')
- `DB_CONNECTION_TIMEOUT`: Connection timeout in milliseconds
- `DB_REQUEST_TIMEOUT`: Request timeout in milliseconds
- `DB_POOL_MAX`: Maximum pool size
- `DB_POOL_MIN`: Minimum pool size
- `DB_POOL_IDLE_TIMEOUT`: Pool idle timeout in milliseconds

## Priority

Command-line arguments take precedence over environment variables, which take precedence over the default values.

## Example Usage

```bash
# Using command-line arguments
node server.mjs --host my-sql-server.database.windows.net --database my_project_db --username admin --password mySecurePassword123

# Using environment variables (Linux/macOS)
DB_SERVER=my-sql-server.database.windows.net DB_DATABASE=my_project_db DB_USER=admin DB_PASSWORD=mySecurePassword123 node server.mjs

# Using environment variables (Windows CMD)
set DB_SERVER=my-sql-server.database.windows.net
set DB_DATABASE=my_project_db
set DB_USER=admin
set DB_PASSWORD=mySecurePassword123
node server.mjs

# Using environment variables (Windows PowerShell)
$env:DB_SERVER="my-sql-server.database.windows.net"
$env:DB_DATABASE="my_project_db"
$env:DB_USER="admin"
$env:DB_PASSWORD="mySecurePassword123"
node server.mjs
```

## Using with Different Projects

For different projects, you can create batch files or shell scripts to set the appropriate connection parameters:

### Windows (project1.bat)
```batch
@echo off
node server.mjs --host project1-server.database.windows.net --database project1_db --username project1_user --password project1_password
```

### Linux/macOS (project1.sh)
```bash
#!/bin/bash
node server.mjs --host project1-server.database.windows.net --database project1_db --username project1_user --password project1_password
```

This approach allows you to easily switch between different database configurations without modifying the code. 