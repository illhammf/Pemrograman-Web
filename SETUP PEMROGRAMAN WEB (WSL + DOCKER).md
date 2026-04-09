# 📘 SETUP PEMROGRAMAN WEB (WSL + DOCKER + LARAVEL)

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

### Install Ubuntu & Terminal

- Install Ubuntu dari Microsoft Store
- Install Windows Terminal

---

## ⚙️ 2. Set WSL ke WSL2 & ROOT

Buka PowerShell (Run as Administrator):

```bash
wsl --set-default-version 2
ubuntu config --default-user root
🔧 3. Konfigurasi WSL (WAJIB)

Edit file:

nano /etc/wsl.conf

Isi konfigurasi:

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

Restart WSL:

wsl --shutdown
📦 4. Install Dependencies
apt update && apt upgrade -y
apt install git -y
apt install python3 python3-pip -y
apt install default-jdk -y
apt install plantuml -y
apt install jq -y
💻 5. Setup ZSH (Optional)
apt install zsh -y
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

Install plugin:

git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting $ZSH_CUSTOM/plugins/zsh-syntax-highlighting

Edit config:

nano ~/.zshrc

Ubah:

plugins=(git)

Menjadi:

plugins=(git zsh-autosuggestions zsh-syntax-highlighting)

Reload:

source ~/.zshrc
🔐 6. Setup GitHub SSH
ssh-keygen -t rsa -b 4096 -C "emailkamu@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub

Tambahkan ke GitHub:

Settings → SSH Keys → Add New Key

Test koneksi:

ssh -T git@github.com
📂 7. Clone Repository
cd ~
git clone git@github.com:djambred/boilerplate.git
cd boilerplate
🔑 8. Setup GitHub Token

Buka:
https://github.com/settings/tokens

Buat:
Token Classic
No expiration
Centang:
repo
user
delete_repo

Simpan ke file:

touch .github-token
touch .github-user

Isi:

.github-token → token
.github-user → username GitHub

⚠️ Jangan upload file ini ke GitHub!

🚀 9. Jalankan Project
./start.sh pemweb
⚠️ Troubleshooting
❌ mkcert tidak ditemukan
apt install mkcert -y
mkcert -install
❌ Permission denied (publickey)
SSH belum dikonfigurasi dengan benar
❌ Docker build lama
Normal (5–20 menit)
❌ Docker tidak jalan
Pastikan Docker Desktop aktif
🔄 10. Reload Environment
source /root/.zshrc
⚡ 11. Command Shortcut
Command	Fungsi
dcu	docker-compose up -d
dcd	docker-compose down
dci	init project
dcp	git add + commit + push
dca	php artisan
🌐 12. Akses Project

Buka di browser:

https://localhost
📂 13. Struktur Project
Folder	Fungsi
src	Laravel
nginx	Web server
php	PHP config
db	Database
docker-compose.yml	Docker config
💻 14. Buka di VS Code
cd /root/perkuliahan/crkosongdua
code .
```
