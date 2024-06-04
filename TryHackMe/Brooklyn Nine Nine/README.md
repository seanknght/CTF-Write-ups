This box is beginner friendly, you can find the room here.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/599ff6e1-1036-49fd-8b02-3dd96109173a)

# The Contents of the Room:
Task 1: User flag
Task 2: Root flag
# Scanning

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/ad0aefa7-0573-4d06-b69e-8597fc15d6aa)

We see that that 3 ports are open, port 21 ftp, port 22 ssh and port 80 http. Let's see what’s on port 21 ftp?

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/6ec9bc3a-c97f-4d02-9378-10f26d7c1c20)

We are able to login anonymously and their is file called note_to_jake.txt that we can download.

# FTP Login
![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/abe5c5af-7335-4033-9a1b-969da3255c47)

the login name is anonymous and the password is anonymous. Now ls -la to list all the contents and get note_to_jake.txt to download the file to your machine. You can use the command exit to exit ftp or open another terminal window to read the file.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/8953edd9-e780-46ca-9dda-da845f9b9796)

Jake seems to have a weak password. Lets see if we can brute force our way in with hydra and the rockyou wordlist.

# Password Cracking [Hydra]

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/f5fc74f2-f016-48ff-89dc-8b9dff313cec)

We got Jake’s password, now lets ssh in to look for the first flag.

# SSH Login

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/e7b7982e-2f6c-458f-9149-a982eb8c90b4)

The flag is located in holt’s directory.

Answer 1: ee11cbb19052e40b07aac0ca060c23ee

Now let's try to di privilege escalation to get the root flag.

First let's run the command sudo -l to find any binaries we can run as sudo.

We found less, lets search for it on gtfobins.

# Privilege Escalation

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/cd2f1244-5fa0-4c34-9387-1c412e10e294)

Great, now copy and paste it as it is in Jake@brookly_nine_nine and press enter.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/cf8c54ad-7f61-42b5-b77c-1c9386d6a9fe)

If you see this press enter again.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/a9859f71-9885-4073-9d43-53e53f9ce4af)

Now type command whoami, it should say root if successful. Now the Root flag is located in the root directory, type cd /root and then cat root.txt.

Answer 2: 63a9f0ea7bb98050796b649e85481845

I hope you find this walkthrough helpful in completing the room! If you are still struggling feel free to message me on Instagram and I will try my best to assist!
