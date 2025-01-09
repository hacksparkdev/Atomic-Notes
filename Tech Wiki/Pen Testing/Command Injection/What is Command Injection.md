Tags: [[Penetration Testing]] [[Command Injection]] [[Cybersecurity]] #CommandInjection

## References
Html Encoding reference.
https://www.w3schools.com/tags/ref_urlencode.ASP

### Definition
Injections occurs when user-controlled input is misinterpreted as part of the web query or code being executed, which may lead to subverting the intended outcome of the query to a different outcome that is useful to the attacker.

### Most command Injections

- OS Command Injections 
	- Occurs when input is directly used as part of an OS command.
- Code Injection
	- Occurs when user input is directly within a function that evaluates code.
- SQL Injections 
	- Occurs when user input is directly used as part of an SQL query.
- Cross-Site Script/HTML Injection
	- Occurs when exact user input is displayed on a web page.


## Command Injection Methods
#CommandInjection_reference

| **Injection Operator** | **Injection Character** | **URL-Encoded Character** | **Executed Command**                       |
| ---------------------- | ----------------------- | ------------------------- | ------------------------------------------ |
| Semicolon              | `;`                     | `%3b`                     | Both                                       |
| New Line               | `\n`                    | `%0a`                     | Both                                       |
| Background             | `&`                     | `%26`                     | Both (second output generally shown first) |
| Pipe                   | `\|`                    | `%7c`                     | Both (only second output is shown)         |
| AND                    | `&&`                    | `%26%26`                  | Both (only if first succeeds)              |
| OR                     | \|\|                    | `%7c%7c`                  | Second (only if first fails)               |
| Sub-Shell              | ` `` `                  | `%60%60`                  | Both (Linux-only)                          |
| Sub-Shell              | `$()`                   | `%24%28%29`               | Both (Linux-only)                          |

### Most common operator used for injection

![[Screenshot From 2024-12-18 16-48-06.png]]

## Print Environment Variables
```bash
print env

SYSTEMD_EXEC_PID=1850
SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
SESSION_MANAGER=local/kali:@/tmp/.ICE-unix/1816,unix/kali:/tmp/.ICE-unix/1816
GNOME_TERMINAL_SCREEN=/org/gnome/Terminal/screen/1e5d080e_5e43_47fb_89b4_6c113c0156a0
LANG=en_US.UTF-8
XDG_CURRENT_DESKTOP=GNOME
NMAP_PRIVILEGED=
POWERSHELL_UPDATECHECK=Off
IM_CONFIG_PHASE=1
PWD=/home/hackspark
QT_IM_MODULE=ibus
GPG_AGENT_INFO=/run/user/1000/gnupg/S.gpg-agent:0:1
USER=hackspark
DESKTOP_SESSION=gnome
XDG_MENU_PREFIX=gnome-
HOME=/home/hackspark
COMMAND_NOT_FOUND_INSTALL_PROMPT=1
DISPLAY=:1
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
XDG_CONFIG_DIRS=/etc/xdg/xdg-kali-purple:/etc/xdg:
WINDOWPATH=2
XDG_SESSION_DESKTOP=gnome
QT_ACCESSIBILITY=1
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
VTE_VERSION=7801
LOGNAME=hackspark
GNOME_TERMINAL_SERVICE=:1.125
DOTNET_CLI_TELEMETRY_OPTOUT=1
QT_AUTO_SCREEN_SCALE_FACTOR=0
XDG_RUNTIME_DIR=/run/user/1000
XMODIFIERS=@im=ibus
PATH=/home/hackspark/.local/bin:/usr/local/sbin:/usr/sbin:/sbin:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
MEMORY_PRESSURE_WRITE=c29tZSAyMDAwMDAgMjAwMDAwMAA=
POWERSHELL_TELEMETRY_OPTOUT=1
SHELL=/usr/bin/zsh
XDG_SESSION_TYPE=x11
_JAVA_OPTIONS=-Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
USERNAME=hackspark
QT_QPA_PLATFORMTHEME=qt5ct
GDM_LANG=en_US.UTF-8
XAUTHORITY=/run/user/1000/gdm/Xauthority
COLORTERM=truecolor
MEMORY_PRESSURE_WATCH=/sys/fs/cgroup/user.slice/user-1000.slice/user@1000.service/session.slice/org.gnome.Shell@x11.service/memory.pressure
TERM=xterm-256color
GDMSESSION=gnome
XDG_SESSION_CLASS=user
SHLVL=1
OLDPWD=/
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=00:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.7z=01;31:*.ace=01;31:*.alz=01;31:*.apk=01;31:*.arc=01;31:*.arj=01;31:*.bz=01;31:*.bz2=01;31:*.cab=01;31:*.cpio=01;31:*.crate=01;31:*.deb=01;31:*.drpm=01;31:*.dwm=01;31:*.dz=01;31:*.ear=01;31:*.egg=01;31:*.esd=01;31:*.gz=01;31:*.jar=01;31:*.lha=01;31:*.lrz=01;31:*.lz=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.lzo=01;31:*.pyz=01;31:*.rar=01;31:*.rpm=01;31:*.rz=01;31:*.sar=01;31:*.swm=01;31:*.t7z=01;31:*.tar=01;31:*.taz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tgz=01;31:*.tlz=01;31:*.txz=01;31:*.tz=01;31:*.tzo=01;31:*.tzst=01;31:*.udeb=01;31:*.war=01;31:*.whl=01;31:*.wim=01;31:*.xz=01;31:*.z=01;31:*.zip=01;31:*.zoo=01;31:*.zst=01;31:*.avif=01;35:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.webp=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:*~=00;90:*#=00;90:*.bak=00;90:*.crdownload=00;90:*.dpkg-dist=00;90:*.dpkg-new=00;90:*.dpkg-old=00;90:*.dpkg-tmp=00;90:*.old=00;90:*.orig=00;90:*.part=00;90:*.rej=00;90:*.rpmnew=00;90:*.rpmorig=00;90:*.rpmsave=00;90:*.swp=00;90:*.tmp=00;90:*.ucf-dist=00;90:*.ucf-new=00;90:*.ucf-old=00;90::ow=30;44:
LESS_TERMCAP_mb=
LESS_TERMCAP_md=
LESS_TERMCAP_me=
LESS_TERMCAP_so=
LESS_TERMCAP_se=
LESS_TERMCAP_us=
LESS_TERMCAP_ue=
_=/usr/bin/printenv
```
