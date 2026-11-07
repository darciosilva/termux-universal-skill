# Termux Universal Guide

## Introduction
Termux is a terminal emulator and Linux environment for Android. This skill covers everything from basic commands to advanced usage.

## 1. Installation and Initial Setup
- Install from F-Droid or Google Play
- First launch installs minimal base system
- Initial commands: `pkg update`, `pkg upgrade`
- Keyboard customization (if needed)

## 2. SSH Connection with Zafiro
- Requires host, port, username, password
- Default port: 8022
- Start SSH server: `sshd`
- Connection: `ssh username@127.0.0.1 -p 8022`
- Note: SSH server dies when Termux is killed

## 3. Basic Shell Commands
- Navigation: `ls`, `cd`, `pwd`, `mkdir`, `rmdir`, `rm`, `cp`, `mv`, `touch`
- Viewing: `cat`, `less`, `more`, `head`, `tail`
- Search: `grep`, `find`, `which`, `whereis`
- Permissions: `chmod`, `chown`, `chgrp`
- Pipes and redirection: `|`, `>`, `<`, `>>`
- Environment variables: `export`, `echo $VAR`
- History: `history`, `!`, `Ctrl+R`

## 4. Package Management
- `pkg` (wrapper for apt)
- `apt-get`, `apt-cache`, `dpkg`
- Install: `pkg install <package>`
- Update: `pkg update`, `pkg upgrade`
- Remove: `pkg uninstall <package>`
- Search: `pkg search <query>`
- Clean: `pkg clean`
- Sources: edit `/data/data/com.termux/files/usr/etc/apt/sources.list`

## 5. Text Editors
- **nano**: Available by default. Simple, visual interface. Use `Ctrl+X` to exit, `Ctrl+O` to save.
- **vim**: NOT installed by default. Install with `pkg install vim`. Modes: normal, insert, visual.
- **emacs**: NOT installed by default. Install with `pkg install emacs`. Extensible, modes.
- Others: `micro`, `code` (if installed)

## 6. Network Commands
- SSH: `ssh`, `scp`, `sftp`, `ssh-keygen`, `ssh-copy-id`
- Download: `wget`, `curl`
- Network: `ifconfig`, `ip`, `ping`, `netstat`, `ss`, `nmap`, `nc`
- Firewall: `iptables` (if installed)
- VPN: `openvpn` (if installed)

## 7. System Commands
- Processes: `ps`, `top`, `htop`, `kill`, `killall`, `pkill`
- Memory: `free`, `df`, `du`
- System: `uname`, `uptime`, `whoami`, `id`
- Files: `mount`, `umount`, `lsblk`, `fdisk`
- Cron: `crontab` (if installed)

## 8. Development Tools

### Python
- **Version**: Python 3.14.10 (verified)
- **Pip**: `pip3` - package installer
- **Virtualenv**: `virtualenv` or `python3 -m venv` - isolated environments
- **Common packages**: `pip3 install numpy pandas flask django requests`
- **Run scripts**: `python3 script.py`
- **Interactive console**: `python3`

### Node.js
- **Version**: Node.js v26.13.0, npm 12.2.1 (verified)
- **Install packages**: `npm install <package>`
- **Run scripts**: `node script.js`
- **Global packages**: `npm install -g <package>`

### C/C++
- **Compiler**: `clang version 21.1.8` (gcc/g++ are symlinks to clang in Termux)
- **Make**: GNU Make 4.4.1 (verified)
- **CMake**: 4.4.4 (verified)
- **Example**: `gcc -o hello hello.c && ./hello`

### Git
- **Version**: Git 2.56.0 (verified)
- **Clone**: `git clone <url>`
- **Push**: `git push origin main`
- **Pull**: `git pull origin main`
- **Commit**: `git commit -m "message"`
- **Branch**: `git branch`, `git checkout <branch>`

### Perl
- **Version**: Perl 5.42.2 (verified)
- **CPAN**: `cpan` - Perl package manager

### Ruby
- **Version**: Ruby 4.0.7 (verified)
- **Gem**: `gem` - Ruby package manager

### Other Tools (if installed)
- **Rust**: `rustc`, `cargo`
- **Go**: `go`
- **Java**: `javac`, `java`
- **PHP**: `php`, `php-cgi`

## 9. Termux-Specific Commands
- `termux-am`: send am commands
- `termux-clipboard-get/set`: clipboard
- `termux-sms-list/send`: SMS
- `termux-notification-list`: notifications
- `termux-open`, `termux-open-url`: open files/URLs
- `termux-storage-get`: storage access
- `termux-wifi-scaninfo`: Wi-Fi info
- `termux-camera-photo`: camera
- `termux-location`: GPS
- `termux-sensor`: sensors
- `termux-tts-speak`: text-to-speech
- `termux-volume`: volume control
- And many more...

## 10. Advanced Topics
### proot and proot-distro
- `proot`: redirect root without root privileges
- `proot-distro`: run Debian, Ubuntu, Alpine, etc.
- Example: `proot-distro login debian`

### X11 and Graphics
- Install X11: `pkg install x11`
- Start X server: `termux-x11`
- Graphical apps: `firefox`, `chromium`, etc.

### Background Services
- `nohup`, `&`, `screen`, `tmux`
- Scripts for services

### Scripting and Automation
- Bash scripts
- Python scripts
- Cron jobs

### Security
- SSH keys: `ssh-keygen`
- GPG: `gpg`
- Avoid storing passwords in environment variables

## 11. Tips and Tricks
- Keyboard shortcuts
- Shell customization (zsh, bashrc)
- Font installation
- Backup and restore

## 12. Troubleshooting
- Package installation errors
- Permission issues
- SSH connection refused
- Storage access problems


## 13. Storage & Android Interoperability
- **Termux Storage Access**: `termux-setup-storage`
  - Creates `~/storage` directory linking to internal storage.
  - `~/storage/shared` -> `/sdcard`
  - `~/storage/downloads` -> `/sdcard/Download`
  - `~/storage/dcim` -> `/sdcard/DCIM`
  - `~/storage/pictures` -> `/sdcard/Pictures`
- **SAF (Storage Access Framework)**: `termux-saf-*` commands for external SD cards/USB storage.

## 14. Databases
- **SQLite**: `sqlite3` - lightweight zero-config SQL database.
- **MariaDB / MySQL**: `pkg install mariadb` -> initialize with `mariadb-install-db` -> start with `mysqld_safe &`
- **PostgreSQL**: `pkg install postgresql` -> `initdb` -> `pg_ctl -D $PREFIX/var/lib/postgresql start`
- **Redis**: `pkg install redis` -> start with `redis-server`

## 15. Web Servers & Reverse Proxies
- **Nginx**: `pkg install nginx` -> config at `$PREFIX/etc/nginx/nginx.conf` -> start with `nginx`
- **Apache (httpd)**: `pkg install apache2` -> start with `httpd`
- **Caddy**: `pkg install caddy` -> `caddy file-server` or `caddy reverse-proxy`
- **Cloudflare Tunnel**: `cloudflared` for exposing local Termux servers safely without port forwarding.

## 16. Media & Productivity Utilities
- **FFmpeg**: Version 9.0.2 (verified). `ffmpeg -i input.mp4 output.mp3` - audio/video conversion and processing.
- **yt-dlp**: Version 2021.06.01 (verified). `yt-dlp <URL>` - video/audio downloader.
- **ImageMagick**: NOT installed by default. Install with `pkg install imagemagick`. `convert input.jpg output.png` - image manipulation.
- **Pandoc**: NOT installed by default. Install with `pkg install pandoc`. `pandoc input.md -o output.pdf` - document converter.

## 17. Process Management & Background Tasks
- **tmux**: `tmux new -s session_name`, `tmux attach -t session_name` - persistent terminal sessions.
- **screen**: `screen -S session_name` - alternative terminal multiplexer.
- **termux-job-scheduler**: Schedule periodic background jobs natively in Android.
- **Crontab**: `crontab -e` -> periodic automated tasks.

## 18. Root Access (TSU / SU)
- **tsu**: `pkg install tsu` - Termux wrapper for `su` preserving environment.
- **Root commands**: `tsu` or `sudo` (if configured with tsu alias).


## 19. Diagnóstico e Fallback (Quando uma Ferramenta Falha)

Se uma ferramenta falhar ou comportar-se de forma inesperada, siga este fluxo de diagnóstico antes de tentar soluções alternativas:

### Passo 1: Verifique a Versão
```bash
<ferramenta> --version
```
Isso confirma se a versão instalada é compatível com o que você espera.

### Passo 2: Consulte o Help
```bash
<ferramenta> --help
<ferramenta> -h
```
Muitos erros de uso comum (sintaxe incorreta, opções desatualizadas) são revelados pela ajuda.

### Passo 3: Verifique se a Ferramenta está Instalada
```bash
command -v <ferramenta>
```
Se não retornar nada, a ferramenta não está instalada. Instale com:
```bash
pkg install <ferramenta>
```

### Passo 4: Procure por Mensagens de Erro Específicas
Analisando a saída de erro, identifique:
- Permissões insuficientes? Use `tsu` para root.
- Dependências faltando? Use `pkg install` para adicioná-las.
- Caminho incorreto? Verifique com `which` ou `command -v`.

### Exemplo Prático
Se `ffmpeg -i video.mp4 output.mp3` falhar:
1. `ffmpeg -version` → confirma versão
2. `ffmpeg -h` → verifica sintaxe correta
3. `command -v ffmpeg` → confirma instalação
4. Analisa erro: talvez faltando codec? Use `pkg install ffmpeg` para reinstalar.

**Princípio Chave:** Antes de assumir que uma ferramenta está quebrada, verifique sempre a versão e o help. Muitas vezes, o problema é apenas uma opção desatualizada ou um argumento incorreto.
