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

- This page also appears empty but inspecting the source code gives us another directory to check out.

<img width="1128" alt="Capture6" src="https://github.com/user-attachments/assets/1edd3f16-e0a8-4fab-8a8d-b90e264a8ab5" />

<img width="1128" alt="Capture7" src="https://github.com/user-attachments/assets/772f3ce7-3ec7-423f-a5c5-0139d1f6935a" />

- Evidently there is "nothing in this page" so i check the source code again to find what looks like a potential password.

<img width="1128" alt="Capture8" src="https://github.com/user-attachments/assets/50226698-fa35-43df-abac-b757726384d7" />

