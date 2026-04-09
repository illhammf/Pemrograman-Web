# 📘 SETUP PEMROGRAMAN WEB 2026 (WSL + GITHUB + DOCKER)

## 🚀 Deskripsi

Tutorial ini menjelaskan langkah-langkah setup environment Web Development menggunakan:

- WSL (Linux di Windows)
- Docker (Container)
- GitHub (Version Control)
- Laravel (Framework PHP)

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

- Install Ubuntu dari Microsoft Store

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
[automount]
enabled=true
root=/
options="metadata,umask=22,fmask=11"
mountFsTab=true

[network]
hostname=DemoHost
generateHosts=false
generateResolvConf=false

[interop]
enabled=false
appendWindowsPath=false

[user]
default=root

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

Buka di browser untuk tes:

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
