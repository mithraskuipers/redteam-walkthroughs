
```
rustscan -a 192.168.97.5
```


```
PORT   STATE SERVICE REASON
22/tcp open  ssh     syn-ack ttl 64
80/tcp open  http    syn-ack ttl 64
MAC Address: 08:00:27:DB:01:18 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
```


```
nmap -sV -p 22,80 192.168.97.5
```
``
```
Starting Nmap 7.95 ( https://nmap.org ) at 2025-05-10 06:09 EDT
Nmap scan report for 192.168.97.5 (192.168.97.5)
Host is up (0.00049s latency).

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
MAC Address: 08:00:27:DB:01:18 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.48 seconds
```




Browser
192.168.97.5:80

Error

```
# Hmm. We’re having trouble finding that site.
```


sudo nano /etc/hosts

192.168.97.5    deathnote.vuln

In browser
http://deathnote.vuln
Note: without the http, the browser might want to automatically do a Google search on your url

![[Pasted image 20250510122240.png]]

It forwards me to deatnote.vuln/wordpress

This shows there is indeed a webserver running.
Let's see what files and folders can be identified.

```
gobuster dir -u deathnote.vuln/wordpress -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

```

```


```
gobuster dir -u deathnote.vuln/wordpress -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

```

```


---




If you click on HINT you are redirected to



deatnote.vuln/wordpress/index.php/hint




