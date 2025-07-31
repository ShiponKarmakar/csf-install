# 🔥 CSF (ConfigServer Security & Firewall) Installer for cPanel/WHM

This repository provides an easy-to-use, pre-packaged installer for [CSF (ConfigServer Security & Firewall)](https://download.configserver.com/csf.tgz), a popular firewall and security tool for Linux servers. It is fully compatible with cPanel/WHM environments.

---

## 📦 What is CSF?

**CSF** is an advanced firewall, login/intrusion detection, and security suite for Linux servers. It includes:

- 🛡️ Stateful packet inspection  
- 🔐 Login Failure Daemon (LFD)  
- 📬 Email alerts on suspicious activities  
- 🌍 IP blocking and whitelisting  
- 📈 Brute-force attack detection  
- 📦 Port scanning detection

---

## 💻 Installation

### 🚀 Auto Installer (Recommended)

Use this one-liner command to install CSF quickly:

```bash
bash <(curl -sSL https://github.com/ShiponKarmakar/csf-install/raw/main/install.sh)
```

Or (if `curl` is not installed):

```bash
bash <(wget -O - https://github.com/ShiponKarmakar/csf-install/raw/main/install.sh)
```

---

### 🧰 Manual Installation

Step-by-step instructions for manual setup:

#### 1️⃣ SSH into your server

```bash
ssh root@your-server-ip
```

#### 2️⃣ Download the installer package

```bash
wget https://github.com/ShiponKarmakar/csf-install/raw/main/csf.tgz -O csf.tgz
```

#### 3️⃣ Extract the files

```bash
tar -xvzf csf.tgz
cd csf
```

#### 4️⃣ Run the install script

```bash
sh install.sh
```

---

## 🔧 Usage & Configuration

### ✅ Enable CSF from WHM

After install, go to:

```
WHM → Plugins → ConfigServer Security & Firewall
```

- Click **“Enable Firewall”** to activate CSF
- Configure via GUI or edit `/etc/csf/csf.conf`

### 🛠️ Basic Commands

```bash
csf -e       # Enable CSF
csf -x       # Disable CSF
csf -r       # Restart CSF
csf -s       # Start CSF
csf -f       # Flush all rules
csf -g IP    # Search IP in CSF
```

### 📂 Config files

- Main config: `/etc/csf/csf.conf`
- Allow list: `/etc/csf/csf.allow`
- Deny list: `/etc/csf/csf.deny`

---

## 🔄 Updating CSF

Update CSF to the latest version using:

```bash
csf -u
```

---

## ❌ Uninstall CSF

To uninstall CSF completely:

```bash
cd /etc/csf
sh uninstall.sh
```

Then remove any extra files if needed:

```bash
rm -rf /etc/csf
rm -rf /var/lib/csf
```

---

## 🔒 Security Hardening Recommendations

After installation:

- Set `TESTING = "0"` in `/etc/csf/csf.conf`
- Whitelist your IP: `/etc/csf/csf.allow`
- Block unused ports (21, 23, 25, etc.)
- Monitor LFD logs: `tail -f /var/log/lfd.log`
- Enable alerts and rate limits

---

## ⚠️ Troubleshooting

- **Port blocked?** Temporarily disable CSF:

  ```bash
  csf -x
  ```

- **Can’t SSH after install?** Use WHM terminal or VNC/KVM access.
- **Can’t install?** Ensure required packages are present:

  ```bash
  yum install perl iptables -y      # RHEL-based
  apt install perl iptables -y      # Debian-based
  ```

---

## 📬 Maintainer

**👨‍💻  Original file from https://download.configserver.com/csf.tgz

---

## 📄 License

This repository wraps and distributes the original [CSF installer](https://download.configserver.com/csf.tgz) from [ConfigServer](https://configserver.com/).  
CSF is free to use under its original terms. Please respect their license and usage guidelines.

---

## ⭐ Support the Project

- 🌟 Star this repo to support!  
- 🍴 Fork to contribute or improve!  
- 🔧 Submit pull requests or issues!
