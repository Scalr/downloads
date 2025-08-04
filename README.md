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

## Additional Resources
* [Scalr Official Documentation](https://docs.scalr.io/docs/introduction)

* [Scalr Support](https://www.scalr.com/help-center)