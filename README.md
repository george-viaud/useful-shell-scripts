# Useful Scripts Collection

A curated collection of utility scripts that make system administration and development tasks easier. Each script is self-contained, well-documented, and solves a specific problem.

## Scripts

### mountssh

A flexible SSHFS mounting utility that simplifies remote filesystem access.

```bash
mountssh hostname remotepath [--user=username]
```

**Features:**
- Mount remote directories with a simple command
- Uses your SSH config for hostname resolution and connection settings
- Switch to different users on the remote system (requires sudo)
- Automatic home directory resolution
- Persistent mounts with auto-reconnection
- Colored output with clickable directory links
- Prevents duplicate mounts

**Requirements:**
- SSHFS installed locally
- SSH access to remote system
- Sudo access on remote system (for --user option)

**Example Usage:**
```bash
# Mount your home directory using a host from your SSH config
mountssh dev-server ~/

# Mount using full hostname
mountssh user@example.com /var/www

# Mount a web directory as www-data user
mountssh myserver /var/www --user=www-data
```

Mounts are created under `~/ssh-mounts/` with automatic directory naming based on the remote user and hostname. The script uses your SSH configuration file (`~/.ssh/config`), so any hosts, identity files, and connection settings defined there will work automatically.

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/useful-scripts.git
```

2. Make the scripts executable:
```bash
chmod +x useful-scripts/*
```

3. Add to your PATH or symlink to a directory in your PATH:
```bash
# Option 1: Add to PATH in your .bashrc or .zshrc
export PATH="$PATH:/path/to/useful-scripts"

# Option 2: Symlink to ~/.local/bin (create if it doesn't exist)
mkdir -p ~/.local/bin
ln -s /path/to/useful-scripts/* ~/.local/bin/
```
