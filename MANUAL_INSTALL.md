# Scalr Agent Installation Guide

This guide provides steps to download, install, configure, and start the **Scalr Agent** on both **Debian-based (Ubuntu, Debian)** and **RHEL-based (CentOS, Rocky Linux, AlmaLinux, Amazon Linux)** systems.

## Download the Scalr Agent Package
Before installing the agent, download the correct package for your system.

### For RHEL-based (RPM) Systems:
Get the list of available packages in the repository:
```bash
curl -s https://api.github.com/repos/Scalr/downloads/contents/agents/rpm | grep '"name":' | sed 's/.*"name": "\(.*\)".*/\1/'
```

Download package:
```bash
curl -s -L https://github.com/Scalr/downloads/raw/main/agents/<RPM_PACKAGE_NAME> -o scalr-agent.rpm
```
### For Debian-based (DEB) Systems:
Get the list of available packages in the repository:

```bash
curl -s https://api.github.com/repos/Scalr/downloads/contents/agents/deb | grep '"name":' | sed 's/.*"name": "\(.*\)".*/\1/'
```

Download package:
```bash
curl -s -L https://github.com/Scalr/downloads/raw/main/agents/<DEB_PACKAGE_NAME> -o scalr-agent.deb
```

Replace `<RPM_PACKAGE_NAME>` and `<DEB_PACKAGE_NAME>` with the actual package file name from the repository.

## Install the Scalr Agent

Once downloaded, install the package using the appropriate package manager.

### For RHEL-based (RPM) Systems:

```bash
sudo yum install -y ./scalr-agent.rpm
```
Or if using `dnf`:
```bash
sudo dnf install -y ./scalr-agent.rpm
```
### For Debian-based (DEB) Systems:
```bash
sudo dpkg -i scalr-agent.deb
```

If there are missing dependencies, run:
```bash
sudo apt-get install -f
```
