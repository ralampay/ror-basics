# Command Line Basics

## Navigation
- `pwd` – Print working directory
- `ls` – List files in the current directory
- `cd <directory>` – Change directory
- `cd ..` – Move up one directory level
- `cd -` – Switch to the previous directory

## File and Directory Management
- `touch <file>` – Create a new empty file
- `mkdir <directory>` – Create a new directory
- `rm <file>` – Remove a file
- `rm -r <directory>` – Remove a directory and its contents
- `cp <source> <destination>` – Copy files or directories
- `mv <source> <destination>` – Move or rename files

## Viewing and Editing Files
- `cat <file>` – View file contents
- `less <file>` – View file contents with scrolling
- `nano <file>` – Edit a file using Nano editor
- `vim <file>` – Edit a file using Vim editor

## Process Management
- `ps aux` – Show running processes
- `top` – Display active processes dynamically
- `kill <PID>` – Kill a process by its ID
- `killall <name>` – Kill all processes with a specific name

## System Information
- `uname -a` – Show system information
- `df -h` – Show disk space usage
- `du -sh <directory>` – Show size of a directory
- `free -h` – Show memory usage

## Permissions
- `chmod <mode> <file>` – Change file permissions
- `chown <user>:<group> <file>` – Change file ownership

## Networking
- `ping <host>` – Test connectivity to a host
- `curl <URL>` – Fetch a URL
- `wget <URL>` – Download a file
- `ifconfig` / `ip a` – Show network interfaces

## Searching and Finding
- `grep '<pattern>' <file>` – Search for a pattern in a file
- `find <path> -name <filename>` – Find files by name
- `locate <filename>` – Find files quickly (requires `updatedb` command first)

## Archiving and Compression
- `tar -cvf archive.tar <files>` – Create a tar archive
- `tar -xvf archive.tar` – Extract a tar archive
- `gzip <file>` – Compress a file
- `gunzip <file.gz>` – Decompress a file

## User Management
- `whoami` – Show current user
- `who` – Show logged-in users
- `sudo <command>` – Execute a command as root
- `passwd` – Change user password

## Miscellaneous
- `echo "text"` – Print text to terminal
- `history` – Show command history
- `alias ll='ls -la'` – Create a shortcut for a command
- `clear` – Clear terminal screen

## Exiting
- `exit` – Close terminal session
- `logout` – Log out from the current session
