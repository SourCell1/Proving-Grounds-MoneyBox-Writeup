# Proving-Grounds-MoneyBox-Writeup
CTF writeup for MoneyBox on Proving Grounds

- Nmap

kali@kali:~ $ nmap -sC -sV -p- --min-rate 5000 192.168.187.230
Starting Nmap 7.93 ( https://nmap.org ) at 2025-03-03 22:57 EST
Nmap scan report for 192.168.187.230
Host is up (0.094s latency).
Not shown: 65161 filtered tcp ports (no-response), 371 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_-rw-r--r--    1 0        0         1093656 Feb 26  2021 trytofind.jpg
| ftp-syst:
|   STAT:
| FTP server status:
|      Connected to ::ffff:192.168.45.190
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey:
|   2048 1e30ce7281e0a23d5c28888b12acfaac (RSA)
|   256 019dfafbf20637c012fc018b248f53ae (ECDSA)
|_  256 2f34b3d074b47f8d17d237b12e32f7eb (ED25519)
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
|_http-title: MoneyBox
|_http-server-header: Apache/2.4.38 (Debian)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel     

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 37.84 seconds
kali@kali:~ $ 

- Ftp looks interesting so I check for anonymous login


