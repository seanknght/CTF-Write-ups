![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/a7d0d14f-9799-47e0-9062-842b855e2757)

# The Contents of the Room:

1. What is the secret spicy soup recipe?
2. What are the contents of user.txt?
3. What are the contents of root.txt?

# Scanning

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/df99ef07-4598-4a28-8f0e-743655afa7cc)

The scan shows 3 ports are open on this machine, Port 21 FTP, Port 22 SSH and Port 80 HTTP. The scan also reveals that we are able to anonymously login to FTP and it has a directory named ftp that is writeable. There is also a image file and a text file.

# Ftp

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/38a043a1-fca7-438a-83e2-fa6acba7a7f4)

I downloaded to files from the ftp server then displayed the contents of the notice.txt file. Its a complaint about uploading among us images to the website and they suspect Maya. We got a name from this file that may come in handy. Let's have a look at the image file.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/66a148d1-cb70-4569-9772-03b671a0b890)

The image file turns out to be a meme.

# Getting a reverse shell

The ftp directory in the ftp server is writeable. Let's see if we can upload a reverse shell and see if we can a connection, but first let's see whats on port 80.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/ba2962e8-52ab-4246-97fa-b373c0de87bb)

There is a message from the development team that they are still developing the website and they are look for a web developer. Let's run a Gobuster scan for hidden directories.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/91a85465-2c2b-47d5-a3a3-30986f63fea3)

The scan found a directory called /files, lets see whats there.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/8af77b57-b976-47c6-8803-e58ef56fd35a)

It has the same contents as the ftp server, but we have access to the writeable ftp directory. Lets upload the reverse sell payload and try to get a call back to a listener on my machine.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/5942cd22-11cc-4674-8613-0e514808eaba)

The payload is uploaded now lets start the listener and call it in the browser.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/142ceaff-4b33-41d2-86c4-30743374238c)

We got a the shell and stabilized it using /usr/bin/script -qc /bin/bash /dev/null

# Enumerating the machine

Lets have a look around. I checked the directory we landed in and it's the root file directory of the machine. I listed the contents and found a text file called recipe.txt file, displayed its contents and found the answer to the first task. Now lets look for the user flag.

# USER FLAG

Lets look around in the user home directory.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/2a40433e-cb19-42ec-aa53-9450562ed4a2)

We found the directory of a user named Lennie but we do not have permission to access the directory. Lets have another look around.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/a65ff53b-e8c8-4249-b0f1-a3ae8144f30a)

I noticed a suspicious directory called incidents, I listed the contents of the directory and found a pcapng file called suspicious.pcapng. I copied it to the ftp folder on the server and put it on my machine. I opened the file with wireshark and found the logs with a user entering an incorrect password.

# Privilege Escalation

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/a6bde3df-c1a7-4631-8901-a7c1d21fae76)

The password worked to switch to the user lennie and get the user flag in lennie's dirctory.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/61606ba1-5b9e-4545-89fa-10686f5b2a97)

# ROOT FLAG

The hint for the root flag is scripts. So I took a look at the scripts directory in lennies home directory, it contained 2 files, the one that stands out the most is planner.sh. I displayed its contents and it echos another bash file called print.sh in the /etc directory. 

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/4409b1c9-aca7-4ca5-b157-d660108e0470)

I checked and saw that lennie had rwx permission to the file and I upload a reverse shell and set up a listener on my machine.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/03b633b9-9ae6-43f0-8506-f8c6af12d7fc)

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/b5f37fed-c439-4277-a04d-672871d3319a)

It took a minute but we got the shell and found the root flag.

![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/66eb8783-2274-4ac2-8fa4-ab384eeea102)
















