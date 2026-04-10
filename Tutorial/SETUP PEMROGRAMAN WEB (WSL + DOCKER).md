# 📘 SETUP PEMROGRAMAN WEB 2026 (WSL + GITHUB + DOCKER)
---
## 🚀 Deskripsi

Tutorial ini menjelaskan langkah-langkah setup environment Mata Kuliah Web Development menggunakan:

- WSL (Linux di Windows)
- Visual Studio Code System
- Docker (Container)
- GitHub (Version Control)
- Laravel (Framework PHP)

---

## 🚫 PERINGATAN!!!

- Jangan pakai jaringan Esa Unggul (Wifi/LAN)
- Pastikan Jaringan kamu stabil dan tidak LAG
- Siapkan Kuota yang banyak karena akan download banyak hal
- Sudah menginstall Visual Studio Code System, Docker, Navicat v17 dari Djambred

## 🌐 TOOLS PERKULIAHAN
1. WSL
2. Docker (https://www.docker.com)
3. Navicat (https://shared.djncloud.my.id/tools_tempur/)
4. VSCode (https://code.visualstudio.com/download)
5. Github (https://github.com)
6. VPS (sewa 3 bulan)
7. Domain (sewa 1 tahun)
8. Cloudflared (https://www.cloudflare.com)

---
kalo sudah SIAP, kita gass lanjut ke tahapannya hehe
---

## 🧩 1. Install WSL

### Langkah:

1. Buka **Settings → System → Optional Features**
2. Klik **More Windows Features**
3. Centang:
   - Virtual Machine Platform
   - Windows Subsystem for Linux
4. Restart komputer

### Install Ubuntu

- **Install Ubuntu dari Microsoft Store**

---

## ⚙️ 2. Set WSL ke WSL2 & ROOT

Buka PowerShell (Run as Administrator):

```sh
wsl --set-default-version 2
```

---

## 🔧 3. Konfigurasi WSL (WAJIB)

**Edit file:**

```sh
nano /etc/wsl.conf
```
nanti sekalian ganti jika kamu masih **user**, ganti jadi **root**

**Isi konfigurasi (copy semua dan masukkan kedalamnya):**

```bash
# Sets the directory where fixed drives will be automatically mounted. This example changes the mount location, so your C-d>
root = /

# DrvFs-specific options can be specified.
options = "metadata,uid=1003,gid=1003,umask=077,fmask=11,case=off"

# Sets the `/etc/fstab` file to be processed when a WSL distribution is launched.
mountFsTab=true

# Network host settings that enable the DNS server used by WSL 2. This example changes the hostname, sets generateHosts to >
[network]
hostname=DemoHost
generateHosts=false
generateResolvConf=false

# Set whether WSL supports interop processes like launching Windows apps and adding path variables. Setting these to false >
[interop]
enabled=false
appendWindowsPath=false

# Set the user when launching a distribution with WSL.
[user]
default=DemoUser

# Set a command to run when a new WSL instance launches. This example starts the Docker container service.
[boot]
command=service docker start

```

**Restart WSL:**
Jalankan ini di PowerShell, jangan di WSL!!!
```sh
wsl --shutdown
```

---

## 📦 4. Install Dependencies

```bash
apt update && apt upgrade -y
apt install git -y
apt install python3 python3-pip -y
apt install default-jdk -y
apt install plantuml -y
apt install jq -y
```

---

## 💻 5. Setup ZSH (Optional biar Ganteng)

### ZSH
```bash
apt install zsh -y
```

### oh my Zsh
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

**Install plugin:**

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
```

**Edit config:**

```sh
nano ~/.zshrc
```

Ubah:

```sh
plugins=(git)
```

Menjadi:

```sh
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

**Reload:**

```sh
source ~/.zshrc
```

---

## 🔐 6. Setup GitHub SSH

```bash
ssh-keygen -t rsa -b 4096 -C "emailkamu@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub
```

Tambahkan ke GitHub:

**Settings → SSH Keys → Add New Key**

Test koneksi:

```sh
ssh -T git@github.com
```

---

## 📂 7. Clone Repository

```bash
cd ~
git clone git@github.com:djambred/boilerplate.git
cd boilerplate
```

---

## 🔑 8. Setup GitHub Token

Buka:
https://github.com/settings/tokens

Buat:

```sh
Token Classic
No expiration
```

Centang:

- repo
- user
- delete_repo

**Simpan ke file:**

```sh
nano .github-token
nano .github-user
```
**Isi:**

```sh
.github-token → token
.github-user → username GitHub kamu
```

**⚠️ Jangan upload file ini ke GitHub!**

---

## 🚀 9. Jalankan Project

```bash
./start.sh pemweb
```

atau

```sh
./start.sh crkosongdua
```
ini disesuaikan sesuai kelas masing-masing, bisa ***crkosongsatu*** atau ***crkosongdua***

**⚠️ Troubleshooting**
❌ mkcert tidak ditemukan

```sh
apt install mkcert -y
mkcert -install
```

❌ Permission denied (publickey)
```sh
SSH belum dikonfigurasi dengan benar
```

❌ Docker build lama
```sh
Normal (5–20 menit)
```

❌ Docker tidak jalan
```sh
Pastikan Docker Desktop aktif
```

---

## 🔄 10. Reload Environment

```sh
source /root/.zshrc
```

---

## ⚡ 11. Command Shortcut

_Command Fungsi_

```bash
- dcu	docker-compose up -d
- dcd	docker-compose down
- dci	init project
- dcp	git add + commit + push
- dca	php artisan
```

---

## 🌐 12. Akses Project

Buka di ini browser untuk tes:

```sh
crkosongdua.test / crkosongsatu.test
```
Jika Keluar halaman Laravel, berarti BERHASIL
Jika tidak, cek ulang siapa tau ada kesalahan (kalo bingung tanya AI)
---

## 📂 13. Struktur Project

_Folder Fungsi_

- src Laravel
- nginx Web server
- php PHP config
- db Database
- docker-compose.yml Docker config

---

## 💻 14. Buka di VS Code

```sh
cd /root/perkuliahan/crkosongdua
code .
```
_pastikan extension untuk WSL sudah dipasang di VSCode kamu!!!_
