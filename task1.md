# Introductory Research Walkthrough
## Task 2  Example Research Question
### In the Burp Suite Program that ships with Kali Linux, what mode would you use to manually send a request (often repeating a captured request numerous times)?:
https://brainly.com/question/25315695?cb=1676085236358
![image](https://user-images.githubusercontent.com/110059218/218236273-1d42e7d7-135b-4c64-87e1-712278ee9945.png)
#### What hash format are modern Windows login passwords stored in?:
![image](https://user-images.githubusercontent.com/110059218/218236351-82c73e80-edec-4c70-a900-b7f39052a4a3.png)
> The user passwords are stored in a hashed format in a registry hive either as an LM hash or as an NTLM hash.
> >các password được mã hóa ở dạng LM hash hoặc NTLM hash nhưng LM hash có tính bảo mật yếu hơn nên thường sẽ dùng NTLM hash.
> >LAN Manager authentication uses a particularly weak method of hashing a user's password known as the LM hash algorithm, stemming from the mid 1980s when viruses transmitted by floppy disks were the major concern.[6] Although it is based on DES, a well-studied block cipher, the LM hash has several weaknesses in its design.[7] This makes such hashes crackable in a matter of seconds using rainbow tables, or in a few minutes using brute force. Starting with Windows NT, it was replaced by NTLM, which is still vulnerable to rainbow tables, and brute force attacks unless long, unpredictable passwords are used, see password cracking.
> >vậy câu trả lời sẽ là NTLM
### What are automated tasks called in Linux?
![image](https://user-images.githubusercontent.com/110059218/218236655-aa1912b9-865a-4474-8a0c-884ffef0e8cb.png)
>cron jobs có tác dụng giúp bạn làm những công việc định kì, tự động hóa trên linux
### What number base could you use as a shorthand for base 2 (binary)?
>hệ cơ số hexa 2^4 nên chúng ta có thể nhóm 4 bit của hệ 2 thành 1 số trong hệ cơ số hexa
### If a password hash starts with $6$, what format is it (Unix variant)?
![image](https://user-images.githubusercontent.com/110059218/218236799-927738c9-f9ac-4340-8667-b29cad901e09.png)
## What is the CVE for the 2020 Cross-Site Scripting (XSS) vulnerability found in WPForms?
> search CVE mitre: WPForms 2020 thu được:
![image](https://user-images.githubusercontent.com/110059218/218236946-534f28da-409b-419d-8579-971ae38d9107.png)
### There was a Local Privilege Escalation vulnerability found in the Debian version of Apache Tomcat, back in 2016. What's the CVE for this vulnerability?
![image](https://user-images.githubusercontent.com/110059218/218236984-92bd9700-3c2f-4310-9d40-37482641da6c.png)
### What is the very first CVE found in the VLC media player?
![image](https://user-images.githubusercontent.com/110059218/218237057-5acda158-390a-480c-8f27-2f738bcc9f57.png)
### If you wanted to exploit a 2020 buffer overflow in the sudo program, which CVE would you use?
![image](https://user-images.githubusercontent.com/110059218/218237293-0824820d-e33e-49d6-9bdf-87799b4df425.png)
![image](https://user-images.githubusercontent.com/110059218/218237305-f4461940-ee75-4d3d-ae5b-bf8c27f737b3.png)
![image](https://user-images.githubusercontent.com/110059218/218237311-4390d6cd-d86c-4521-893d-22b360d0cfd2.png)
##  Manual Pages:
![image](https://user-images.githubusercontent.com/110059218/218237404-efa2a482-6d70-4a76-86d0-bc1175c0f1ad.png)
>fdisk is a command used to view and alter the partitioning scheme used on your hard drive. What switch would you use to list the current partitions?:
![image](https://user-images.githubusercontent.com/110059218/218237507-1b83ce5c-d937-40d0-ba8c-edbfdf3016c8.png)
nano is an easy-to-use text editor for Linux. There are arguably better editors (Vim, being the obvious choice); however, nano is a great one to start with.
>What switch would you use to make a backup when opening a file with nano?
![image](https://user-images.githubusercontent.com/110059218/218237886-b0595467-f575-4182-b5ed-f175e4045dad.png)
>Netcat is a basic tool used to manually send and receive network requests. What command would you use to start netcat in listen mode, using port 12345?
![image](https://user-images.githubusercontent.com/110059218/218237935-05e946f8-eea6-41c3-8d8d-ffb14eca7346.png)

# LinuxFundamentalsPart1
## A Bit of Background on Linux
### Research: What year was the first release of a Linux operating system?
![image](https://user-images.githubusercontent.com/110059218/218238086-078971af-62db-455e-b6ec-af3ad562656e.png)
### Running Your First few Commands
>If we wanted to output the text "TryHackMe", what would our command be?: echo TryHackMe
### What is the username of who you're logged in as on your deployed Linux machine?
![image](https://user-images.githubusercontent.com/110059218/218238176-5ba9abf4-df6b-479b-9da0-4fc37e920f2d.png)
## Interacting With the Filesystem!
![image](https://user-images.githubusercontent.com/110059218/218238443-4ee66114-e8f0-4f22-ad3b-437034ab09c8.png)
![image](https://user-images.githubusercontent.com/110059218/218238464-4a5fe5a2-4c5a-4308-a1cc-3eab106880f5.png)
## Searching for Files
![image](https://user-images.githubusercontent.com/110059218/218238552-31c07662-ec7a-4154-8c99-c1199811a29c.png)
![image](https://user-images.githubusercontent.com/110059218/218238559-6d9467fb-4cd1-4f14-8072-f778d8244070.png)
## An Introduction to Shell Operators
![image](https://user-images.githubusercontent.com/110059218/218238892-d55b3c5c-ba23-46d0-9618-154db8c2084d.png)
# LinuxFundamentalsPart2
## Introduction to Flags and Switches
![image](https://user-images.githubusercontent.com/110059218/218239973-9ee543ea-7fa5-4767-a47c-fbf406e58894.png)
![image](https://user-images.githubusercontent.com/110059218/218239982-b6104382-bb8b-438e-8646-681e91092641.png)
## Filesystem Interaction Continued
![image](https://user-images.githubusercontent.com/110059218/218240133-ca643b49-4b57-47eb-ab3b-406dee3075b1.png)
## Permissions 101
![image](https://user-images.githubusercontent.com/110059218/218240189-fb864f8d-ce0b-4da0-809f-866fa7627089.png)
## Common Directories
![image](https://user-images.githubusercontent.com/110059218/218242522-a56b74c1-059e-4e4a-b084-6d2b8b6b35b2.png)
# LinuxFundamentalsPart3
## Terminal Text Editors
![image](https://user-images.githubusercontent.com/110059218/218243016-2f2cc41a-861b-4764-9a28-3c0e0593105a.png)
## General/Useful Utilities
![image](https://user-images.githubusercontent.com/110059218/218243425-ffe9d3bd-0554-441d-933c-9ceace45fb49.png)
## Processes 101
![image](https://user-images.githubusercontent.com/110059218/218244391-5bebce7d-114f-404e-a877-2a2d9d0d6366.png)
## Maintaining Your System: Automation
![image](https://user-images.githubusercontent.com/110059218/218244906-f4a417c8-e0ba-4cf9-bbef-706576f2b7a2.png)
## Maintaining Your System: Package Management
![image](https://user-images.githubusercontent.com/110059218/218245541-11fffe93-48a3-481f-afef-8eae35b67279.png)
