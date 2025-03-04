# Proving-Grounds-MoneyBox-Writeup
CTF writeup for MoneyBox on Proving Grounds

- Nmap

<img width="613" alt="Capture2" src="https://github.com/user-attachments/assets/508cf8bd-445a-4adc-a679-41426a95af1e" />

- Ports 21, 22,  and 80 are all open.

- Port 80

<img width="1128" alt="Capture3" src="https://github.com/user-attachments/assets/4edc3909-ae89-4d64-b9a0-ca07d3bd2ff2" />

- Nothing much on the main page so I fuzz directories with dirb.

<img width="451" alt="Capture4" src="https://github.com/user-attachments/assets/e9b0fb66-99cb-4a5a-849c-83878569cbdc" />

- The endpoint /blogs could be interesting.

<img width="1128" alt="Capture5" src="https://github.com/user-attachments/assets/8b7f67e7-ac44-4d72-83ce-fcabacbe06ba" />

- This page also appears empty but inspecting the source code gives us another directory to look at.

<img width="1128" alt="Capture6" src="https://github.com/user-attachments/assets/1edd3f16-e0a8-4fab-8a8d-b90e264a8ab5" />

<img width="1128" alt="Capture7" src="https://github.com/user-attachments/assets/772f3ce7-3ec7-423f-a5c5-0139d1f6935a" />

- Evidently there is "nothing in this page" so i check the source code again to find what looks like a potential password.

<img width="1128" alt="Capture8" src="https://github.com/user-attachments/assets/50226698-fa35-43df-abac-b757726384d7" />

- There isn't much else interesting on the main page so I check out port 21.
- Unauthenticated anonymous login is allowed which grants us access to the ftp server. There is an image file called trytofind.jpg which I'll download to inspect further. Additionally i check if i can upload files back to the server which is not permitted.

<img width="1126" alt="Capture9" src="https://github.com/user-attachments/assets/313cc1a6-9966-4c48-a68b-a13d4382d6bb" />

- I assume steganography is involved here since all clues point towards this png being important, so i run steghide on the file with the secret key I was given earlier.

<img width="556" alt="Capture10" src="https://github.com/user-attachments/assets/b6e6b01b-9007-4aec-887b-d9c9f004bf07" />

- With that we have a username
- The message said renu's password is "weak" so it's likely we can simply brute force our way in using rockyou.txt and hydra.

<img width="1128" alt="Capture11" src="https://github.com/user-attachments/assets/a7d288a8-0e6d-40d8-ac6a-3497ea6fd674" />

- Now we can apply these credentials to the ssh server and get the first flag.

<img width="523" alt="Capture12" src="https://github.com/user-attachments/assets/06ef1b1f-4794-4df0-ad29-8ba48cf2de08" />

- Enumeration
- The first thing I do is run the linpeas script to get a better idea of what we're working with and maybe find some simple Privilege Escallation footholds.

<img width="1128" alt="Capture13" src="https://github.com/user-attachments/assets/1e0827b1-c6d1-4902-8ef0-1094fae93ec6" />

- Linpeas finds that another user on the system has renu's ssh key in their "authorized_keys" file, meaning we should just be able to login without a password since we are already logged in as renu

<img width="1128" alt="Capture14" src="https://github.com/user-attachments/assets/3aa18a1d-d699-4ba9-b4cb-b4dfee845b78" />

<img width="500" alt="Capture15" src="https://github.com/user-attachments/assets/ffb4b94a-bcef-41f9-b63c-93205f0caa76" />

- Now I run "sudo -l" to see if there are any commands I can execute with root perissions.

<img width="659" alt="Capture16" src="https://github.com/user-attachments/assets/b73bd33c-b4ec-4e64-a09a-41ce6c0a83e1" />

- Under lily's account it displays I can run perl as root. The next step is to check GTFObins and figure out what I can do with that.

<img width="1128" alt="Capture17" src="https://github.com/user-attachments/assets/73806b88-4a23-4270-b1ab-533b915d6339" />

- Following the directions on GTFObins escalates our privileges to root.

<img width="667" alt="Capture18" src="https://github.com/user-attachments/assets/01619e15-be5d-4fde-a6ba-f370a303e7b6" />
