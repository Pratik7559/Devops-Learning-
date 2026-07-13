# 🐧 Linux for DevOps

## What is Linux?
Linux is an open-source operating system widely used for servers, cloud computing, containers, and DevOps.

# Linux File System
```
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── opt
├── proc
├── root
├── run
├── sbin
├── tmp
├── usr
└── var
```

# Basic Commands

| Command | Description |
|----------|-------------|
| pwd | Show current directory |
| ls | List files |
| ls -l | Long listing |
| ls -a | Hidden files |
| cd | Change directory |
| cd .. | Parent directory |
| whoami | Current user |
| hostname | Host name |
| date | Current date |
| history | Command history |

# File Commands
```bash
touch file.txt
mkdir project
mkdir -p project/java/src
rm file.txt
rm -r folder
cp file1 file2
cp -r folder backup
mv old.txt new.txt
```

# Viewing Files
```bash
cat file.txt
less file.txt
head -5 file.txt
tail -f log.txt
```

# Searching
```bash
find . -name "*.java"
grep -r "docker" .
which java
whereis java
```

# Permissions
```bash
chmod 755 script.sh
chmod +x script.sh
chown user file
```

Permission values

- 7 = rwx
- 6 = rw-
- 5 = r-x
- 4 = r--
- 0 = ---

# Process Commands
```bash
ps -ef
top
kill PID
kill -9 PID
```

# Disk Commands
```bash
df -h
du -sh *
free -h
```

# Networking
```bash
ping google.com
ip addr
ssh user@ip
scp file user@ip:/home
curl https://google.com
wget URL
```

# Services
```bash
systemctl status nginx
systemctl start nginx
systemctl restart nginx
journalctl -u nginx
```

# Package Manager

Ubuntu
```bash
sudo apt update
sudo apt install git
```

RHEL
```bash
sudo yum install git
sudo dnf install git
```

# Top Linux Interview Questions

1. What is Linux?
2. Difference between grep and find?
3. What is chmod?
4. Difference between Hard Link and Soft Link?
5. Difference between cp and mv?
6. What is sudo?
7. What is PATH?
8. Difference between ps and top?
9. What is a process?
10. Explain Linux file permissions.

# Most Used DevOps Commands

```text
pwd
ls -la
cd
mkdir
rm -rf
cp -r
mv
touch
cat
head
tail -f
grep
find
chmod
chown
ps
top
kill
df -h
du -sh
free -h
systemctl
journalctl
ssh
scp
curl
wget
tar
zip
unzip
apt
yum
dnf
history
```
