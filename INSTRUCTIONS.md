# Scalr Agent Installation Guide

This guide provides steps to download, install, configure, and start the **Scalr Agent** on both **Debian-based (Ubuntu, Debian)** and **RHEL-based (CentOS, Rocky Linux, AlmaLinux, Amazon Linux)** systems.

## Download the Scalr Agent Package
Before installing the agent, download the correct package for your system.

### For RHEL-based (RPM) Systems:
```commandline
curl -s -L https://github.com/Scalr/downloads/raw/test-artifacts-branch/artifacts/<RPM_PACKAGE_NAME> -o scalr-agent.rpm
```
### For Debian-based (DEB) Systems:
```commandline
curl -s -L https://github.com/Scalr/downloads/raw/test-artifacts-branch/artifacts/<DEB_PACKAGE_NAME> -o scalr-agent.deb
```

Replace `<RPM_PACKAGE_NAME>` and `<DEB_PACKAGE_NAME>` with the actual package file name from the repository.

## Install the Scalr Agent

Once downloaded, install the package using the appropriate package manager.

### For RHEL-based (RPM) Systems:

```commandline
sudo yum install -y ./scalr-agent.rpm
```
Or if using `dnf`:
```commandline
sudo dnf install -y ./scalr-agent.rpm
```
### For Debian-based (DEB) Systems:
```commandline
sudo dpkg -i scalr-agent.deb
```

If there are missing dependencies, run:
```commandline
sudo apt-get install -f
```
## Configure the Scalr Agent
After installation, configure the agent using your Scalr token.

```commandline
scalr-agent configure \
--token=<YOUR_SCALR_TOKEN> \
--url=https://scalr-iacp.scalr.io/ \
--agent-name=$(hostname)
```
Replace `<YOUR_SCALR_TOKEN>` with your actual Scalr token.

## Start and Enable the Scalr Agent
Once configured, start the Scalr Agent and enable it to start on boot.

### For Systemd-based Systems:

```commandline
sudo systemctl start scalr-agent
sudo systemctl enable scalr-agent
```

### For SysVinit-based Systems (Older Linux Distros):

```commandline
sudo service scalr-agent start
```

## Verify Scalr Agent Status
To check if the agent is running, use:

```commandline
systemctl status scalr-agent
```
Or:
```commandline
scalr-agent status
```
If the agent fails to start, check logs:
```commandline
journalctl -u scalr-agent --no-pager -n 50
```

## Uninstalling the Scalr Agent
If you need to remove the Scalr Agent:

### For RHEL-based Systems:

```commandline
sudo yum remove -y scalr-agent
```
Or:

```commandline
sudo dnf remove -y scalr-agent
```

### For Debian-based Systems:

```commandline
sudo apt-get remove -y scalr-agent
```

To clean up leftover configuration files:

```commandline
sudo rm -rf /etc/scalr-agent /var/lib/scalr-agent
```

## Troubleshooting
* Ensure you have internet access if you encounter issues downloading the package.
* Check firewall rules if the agent cannot connect to https://scalr-iacp.scalr.io/.
* If installation fails, ensure your system is up to date:

```commandline
sudo yum update -y    # RHEL-based
sudo apt-get update   # Debian-based
```

## Additional Resources
* [Scalr Official Documentation](https://docs.scalr.io/docs/introduction)

* [Scalr Support](https://www.scalr.com/help-center)

