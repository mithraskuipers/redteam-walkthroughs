https://www.vulnhub.com/entry/beelzebub-1,742/

sudo netdiscover -i eth0 -r 192.168.97.0/24

```
 Currently scanning: Finished!   |   Screen View: Unique Hosts                                                        
                                                                                                                      
 4 Captured ARP Req/Rep packets, from 4 hosts.   Total size: 240                                                      
 _____________________________________________________________________________
   IP            At MAC Address     Count     Len  MAC Vendor / Hostname      
 -----------------------------------------------------------------------------
 192.168.97.1    52:54:00:12:35:00      1      60  Unknown vendor                                                     
 192.168.97.2    52:54:00:12:35:00      1      60  Unknown vendor                                                     
 192.168.97.3    08:00:27:8e:80:b2      1      60  PCS Systemtechnik GmbH                                             
 192.168.97.6    08:00:27:78:9e:5c      1      60  PCS Systemtechnik GmbH 
```

nmap -sV -p 22,80 192.168.97.6

└─$ nmap -sV -p 22,80 192.168.97.6
Starting Nmap 7.95 ( https://nmap.org ) at 2025-05-21 07:59 EDT
Nmap scan report for 192.168.97.6 (192.168.97.6)
Host is up (0.0035s latency).

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
MAC Address: 08:00:27:78:9E:5C (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.33 seconds


Ports 22 and 80 are open



---

Port 80

![[Pasted image 20250521140825.png]]


---


---


```
gobuster dir -u 192.168.97.6 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```


```
┌──(kali㉿kali)-[~]
└─$ gobuster dir -u 192.168.97.6 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://192.168.97.6
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/javascript           (Status: 301) [Size: 317] [--> http://192.168.97.6/javascript/]
/phpmyadmin           (Status: 301) [Size: 317] [--> http://192.168.97.6/phpmyadmin/]
/server-status        (Status: 403) [Size: 277]
Progress: 220560 / 220561 (100.00%)
===============================================================
Finished
===============================================================
```




```
sudo apt-get update -y ;
sudo apt-get install dirsearch -y ;
```


```
─$ dirsearch -u http://192.168.97.6 -e txt,html,php
```


```
└─$ dirsearch -u http://192.168.97.6 -e txt,html,php
/usr/lib/python3/dist-packages/dirsearch/dirsearch.py:23: DeprecationWarning: pkg_resources is deprecated as an API. See https://setuptools.pypa.io/en/latest/pkg_resources.html
  from pkg_resources import DistributionNotFound, VersionConflict

  _|. _ _  _  _  _ _|_    v0.4.3                                                                                      
 (_||| _) (/_(_|| (_| )                                                                                               
                                                                                                                      
Extensions: txt, html, php | HTTP method: GET | Threads: 25 | Wordlist size: 10403

Output File: /home/kali/reports/http_192.168.97.6/_25-05-21_08-39-45.txt

Target: http://192.168.97.6/

[08:39:45] Starting:                                                                                                  
[08:39:46] 403 -  277B  - /.ht_wsr.txt                                      
[08:39:46] 403 -  277B  - /.htaccess.bak1                                   
[08:39:46] 403 -  277B  - /.htaccess.orig                                   
[08:39:46] 403 -  277B  - /.htaccess.save                                   
[08:39:46] 403 -  277B  - /.htaccess.sample                                 
[08:39:46] 403 -  277B  - /.htaccess_orig                                   
[08:39:46] 403 -  277B  - /.htaccess_sc
[08:39:46] 403 -  277B  - /.htaccess_extra
[08:39:46] 403 -  277B  - /.htaccessOLD2
[08:39:46] 403 -  277B  - /.htaccessOLD                                     
[08:39:46] 403 -  277B  - /.htaccessBAK
[08:39:46] 403 -  277B  - /.htm
[08:39:46] 403 -  277B  - /.html                                            
[08:39:46] 403 -  277B  - /.htpasswd_test                                   
[08:39:46] 403 -  277B  - /.htpasswds                                       
[08:39:46] 403 -  277B  - /.httr-oauth                                      
[08:39:47] 403 -  277B  - /.php                                             
[08:39:58] 200 -  221B  - /index.php                                        
[08:39:58] 200 -  221B  - /index.php/login/                                 
[08:39:58] 301 -  317B  - /javascript  ->  http://192.168.97.6/javascript/  
[08:40:02] 200 -   24KB - /phpinfo.php                                      
[08:40:02] 301 -  317B  - /phpmyadmin  ->  http://192.168.97.6/phpmyadmin/  
[08:40:02] 200 -    3KB - /phpmyadmin/doc/html/index.html                   
[08:40:02] 200 -    3KB - /phpmyadmin/                                      
[08:40:02] 200 -    3KB - /phpmyadmin/index.php                             
[08:40:05] 403 -  277B  - /server-status                                    
[08:40:05] 403 -  277B  - /server-status/                                   
                                                                             
Task Completed
```


http://192.168.97.6/index.php

View page source

![[Pasted image 20250521154515.png]]


This line could be a hint

```
<!--My heart was encrypted, "beelzebub" somehow hacked and decoded it.-md5-->
```

md5 is a hashing function, and beelzebub was written between quotation marks.
Perhaps we need to hash the beelzebub string.

https://www.md5hashgenerator.com/

![[Pasted image 20250521154815.png]]

Output

```
d18e1e22becbd915b45e0e655429d487
```

---

http://192.168.97.6/phpmyadmin/

![[Pasted image 20250521155024.png]]


WIP