# Scalr Downloads

APT and RPM package repositories for Scalr Agent.

---

## Using APT Repository

Add the repository GPG key:

```bash
curl -fsSL https://downloads.scalr.com/pgp-key.public | sudo gpg --dearmor -o /usr/share/keyrings/scalr-keyring.gpg
```

Add the repository to your sources list:

```bash
echo "deb [signed-by=/usr/share/keyrings/scalr-keyring.gpg] https://downloads.scalr.com/apt stable main" | sudo tee /etc/apt/sources.list.d/scalr.list
```

Update and install:

```bash
sudo apt update
sudo apt install scalr-agent
```

---

## Using RPM Repository

Create the repository file:

```bash
sudo tee /etc/yum.repos.d/scalr.repo <<EOF
[scalr]
name=Scalr Agent
baseurl=https://downloads.scalr.com/rpm
enabled=1
gpgcheck=1
gpgkey=https://downloads.scalr.com/pgp-key.public
EOF
```

Install the Scalr Agent:

```bash
sudo yum install scalr-agent
# or for dnf-based systems:
sudo dnf install scalr-agent
```

---

## Manual Installation

If you prefer to manually download and install the Scalr Agent without using package repositories:

[📄 View the manual installation guide](MANUAL_INSTALL.md)

---

## Configure the Scalr Agent
After installation, configure the agent using your Scalr token.

```bash
scalr-agent configure \
--token=<YOUR_SCALR_TOKEN> \
--url=https://scalr-iacp.scalr.io/ \
--agent-name=$(hostname)
```
Replace `<YOUR_SCALR_TOKEN>` with your actual Scalr token.

## Start and Enable the Scalr Agent
Once configured, start the Scalr Agent and enable it to start on boot.

### For Systemd-based Systems:

```bash
sudo systemctl start scalr-agent
sudo systemctl enable scalr-agent
```

### For SysVinit-based Systems (Older Linux Distros):

```bash
sudo service scalr-agent start
```

## Verify Scalr Agent Status
To check if the agent is running, use:

```bash
systemctl status scalr-agent
```
Or:
```bash
scalr-agent status
```
If the agent fails to start, check logs:
```bash
journalctl -u scalr-agent --no-pager -n 50
```

---

## Uninstalling the Scalr Agent
If you need to remove the Scalr Agent:

### For RHEL-based Systems:

```bash
sudo yum remove -y scalr-agent
```
Or:

```bash
sudo dnf remove -y scalr-agent
```

### For Debian-based Systems:

```bash
sudo apt remove -y scalr-agent
```

To clean up leftover configuration files:

```bash
sudo rm -rf /etc/scalr-agent /var/lib/scalr-agent
```

---

## Troubleshooting
* Ensure you have internet access if you encounter issues downloading the package.
* Check firewall rules if the agent cannot connect to https://scalr-iacp.scalr.io/.
* If installation fails, ensure your system is up to date:

```bash
sudo yum update -y # RHEL-based
sudo apt update    # Debian-based
```

## Additional Resources
* [Scalr Official Documentation](https://docs.scalr.io/docs/introduction)

* [Scalr Support](https://www.scalr.com/help-center)