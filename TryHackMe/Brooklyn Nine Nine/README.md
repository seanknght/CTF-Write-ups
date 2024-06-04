![image](https://github.com/seanknght/CTF-Write-ups/assets/149443469/599ff6e1-1036-49fd-8b02-3dd96109173a)

This box is beginner friendly, you can find the room here.


The Contents of the Room:
Task 1: User flag
Task 2: Root flag
Lets run the IP address in Nmap

We see that that 3 ports are open, port 21 ftp, port 22 ssh and port 80 http.

what’s on port 21 ftp?

We are able to login anonymously and their is file called note_to_jake.txt that we can download.


the login name is anonymous and the password is anonymous. Now ls -la to list all the contents and get note_to_jake.txt to download the file to your machine. You can use the command exit to exit ftp or open another terminal window to read the file.


Jake seems to have a weak password. Lets see if we can brute force our way in with hydra and the rockyou wordlist.


We got Jake’s password, now lets ssh in to look for the first flag.


The flag is located in holt’s directory.

Answer 1: ee11cbb19052e40b07aac0ca060c23ee

Now let's try to di privilege escalation to get the root flag.

First let's run the command sudo -l to find any binaries we can run as sudo.

We found less, lets search for it on gtfobins.


Great, now copy and paste it as it is in Jake@brookly_nine_nine and press enter.


If you see this press enter again.


Now type command whoami, it should say root if successful. Now the Root flag is located in the root directory, type cd /root and then cat root.txt.

Answer 2: 63a9f0ea7bb98050796b649e85481845

I hope you find this walkthrough helpful in completing the room! If you are still struggling feel free to message me on Instagram and I will try my best to assist!
