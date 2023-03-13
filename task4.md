# HUNTER
**What is the computer name of the suspect machine?**
phần này kiến thức chủ yếu liên quan đến hkey local machine
* có thể tham khảo tại: [HKEY_LOCAL_MACHINE](https://www.lifewire.com/hkey-local-machine-2625902)

search với keyword: computername registry
![image](https://user-images.githubusercontent.com/110059218/224646446-98b89045-7d76-4bf8-87d5-1c1a12e0c419.png)
dùng công cụ registry explorer
* link tải [tool](https://drive.google.com/file/d/19EW3ZJkz-Qac6Tt1r8suNgBOPAmGkDq1/view?usp=share_link)
![image](https://user-images.githubusercontent.com/110059218/224647405-db32fa7c-40a3-409e-8085-576be996f329.png)
-> đáp án: 4ORENSICS

**What is the computer IP?**
search: computer ip registry và đi theo đường dẫn
![image](https://user-images.githubusercontent.com/110059218/224649182-9347a8d2-8efb-4241-84f8-4a2400912f4b.png)
ip adress: 10.0.2.15

**What was the DHCP LeaseObtainedTime?**
search như các câu trên
thu được kết quả dạng isotime, có thể dùng python convert hoặc dùng tool online
![image](https://user-images.githubusercontent.com/110059218/224698308-6dd8c5b8-19a1-4a64-b9b2-9189809debff.png)
![image](https://user-images.githubusercontent.com/110059218/224698340-7e933091-8815-43ed-bc6e-53e897ca9a5f.png)

**What is the computer SID?**
thực hiện search: computer sid registry

đi theo path
đáp án: S-1-5-21-2489440558-2754304563-710705792-1001

**What is the Operating System(OS) version?**
* computer version registry
![image](https://user-images.githubusercontent.com/110059218/224754224-2b409d75-3259-4628-9ee7-4e875befaf12.png)
![image](https://user-images.githubusercontent.com/110059218/224754302-1c86c8cb-e474-43cf-98d6-cd0c2780f17c.png)
**How many times did this user log on to the computer?**
sử dụng công cụ regripper để phân tích hive lấy thông tin
mục đầu là hive mục thứ 2 là thông tin lấy được xuất ra tệp nào
![image](https://user-images.githubusercontent.com/110059218/224762692-b15cf90a-c543-4038-9677-eea99399b055.png)
![image](https://user-images.githubusercontent.com/110059218/224762750-54126572-78d8-4900-8a5f-af32b1dd7afa.png)
xuống user hunter thì số lần log on là 3

**When was the last login time for the discovered account? Format: one-space between date and time**
lấy last-login của hunter điền vào
![image](https://user-images.githubusercontent.com/110059218/224763723-4842afa0-0bd2-49c6-9fe5-1d49fbbe320e.png)

**There was a “Network Scanner” running on this computer, what was it? And when was the last time the suspect used it? Format: program.exe,YYYY-MM-DD HH:MM:SS UTC**
