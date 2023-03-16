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
![image](https://user-images.githubusercontent.com/110059218/225620331-e107fa16-dfd3-4b68-809d-34f30d3ae779.png)
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

mount ổ lên máy để lấy file prefecth nạp của tool rồi dùng Pecmd để phân tích
![image](https://user-images.githubusercontent.com/110059218/225621414-2c0bbf8b-765a-47bc-88da-370c233dea54.png)
![image](https://user-images.githubusercontent.com/110059218/225622437-efbacf69-f290-4fa9-9e62-f4089d43bb4c.png)
với option -f để chọn file phân tích và path đến file .pf cần phần tích

**When did the port scan end? (Example: Sat Jan 23 hh:mm:ss 2016)**
đọc file lưu lại lịch sử của tool lấy từ root/Windows/Prefetch/ZENMAP.EXE-56B17C4C.pf
![image](https://user-images.githubusercontent.com/110059218/225643581-8f7558df-0f82-4ef4-a503-c46c6e9e0b13.png)
thấy có tổng 1000 port được quét

**What ports were found "open"?(comma-separated, ascending)**

vẫn mở file và đọc như câu trước 

![image](https://user-images.githubusercontent.com/110059218/225650626-61bc1d00-9856-4578-b1bc-ed4f4ac511e2.png)

**What was the version of the network scanner running on this computer?**
![image](https://user-images.githubusercontent.com/110059218/225650762-956f2972-0200-4e7c-a07e-884a6515c450.png)
version của tool thường được lưu ở dữ liệu người dùng

![image](https://user-images.githubusercontent.com/110059218/225650895-655857bb-bf7a-416a-a979-af35e1881b6f.png)
dùng ftk mở và lấy được ver của zenmap: 7.12

**The employee engaged in a Skype conversation with someone. What is the skype username of the other party?**

đầu tiên cần lấy file database của skype về để phân tích
Root/Users/Hunter/AppData/Roaming/Skype/hunterehpt/main.db
ném lên sqlite db chọn db browser để xem từng table

![image](https://user-images.githubusercontent.com/110059218/225661727-619ccae0-cc30-45b5-b0f4-aa9b17c0b0b2.png)

thấy user: hunter có trò chuyện với một người tên là linux-rul3z

**What is the name of the application both parties agreed to use to exfiltrate data and provide remote access for the external attacker in their Skype conversation?**
 
 từ bên trên trích xuất ra đoạn hội thoại trao đổi giữa hai người
 
![image](https://user-images.githubusercontent.com/110059218/225662342-65e57c48-eecd-4bfd-89df-b537b9d92b4f.png)
![image](https://user-images.githubusercontent.com/110059218/225662611-cf34c1d6-0656-471e-8fa0-d2a5c5bdd9e7.png)

nội dung cuộc trao đổi
-> tool họ sử dụng trong cuộc trò chuyện trên là teamviewer

**What is the Gmail email address of the suspect employee?**

chuyển đến table contacts để lấy thông tin của các account 

![image](https://user-images.githubusercontent.com/110059218/225664749-200797b0-9b58-44d4-a746-a6361abf57f9.png)

lấy được email của nhân viên đó

**It looks like the suspect user deleted an important diagram after his conversation with the external attacker. What is the file name of the deleted diagram?**

do đã bị xóa ảnh nên chúng ta phải tìm file backup từ ứng dụng mail nào đó
mò mẫm một lúc thì có thấy một file backup lại ở thư mục document/outlookfile
dùng pst viewer mở ra vào thùng rác có thấy tin nhắn kèm hình ảnh đã bị xóa
![image](https://user-images.githubusercontent.com/110059218/225678624-0e0d9ce2-8925-4d23-88fc-1ec37152c673.png)
**The user Documents' directory contained a PDF file discussing data exfiltration techniques. What is the name of the file?**

vào Documents tìm file và search google thì có kết quả file pdf Ryan_VanAntwerp_thesis.pdf viết về các kỹ thuật đánh cắp dữ liệu

![image](https://user-images.githubusercontent.com/110059218/225679290-8a060c55-5c3a-4693-a006-86e05c410755.png)

**What was the name of the Disk Encryption application Installed on the victim system? (two words space separated)**

sau khi kiểm tra một lúc, có tìm được bcwipe
* bcwipe xóa sạch dữ liệu ra khỏi disk
vào log unistall tìm tên tool 
![image](https://user-images.githubusercontent.com/110059218/225687787-06879332-6c6d-4eb9-86b4-2d1dd2e608e8.png)

-> crypto swap

**What are the serial numbers of the two identified USB storage?**
câu này là một câu liên quan đến registry
tham khảo [tại](https://whitehat.vn/threads/computer-forensics-trich-luc-cac-ket-noi-usb-da-gan-vao-may-tinh-cua-ban.13676/)

![image](https://user-images.githubusercontent.com/110059218/225688222-dd8ba65f-150c-4b8c-ade6-41b1f2e5ea1a.png)

đi theo đường dẫn trên tìm thấy 2 usb kết nối vói máy đáp án là 2 serial của 2 cái usb

![image](https://user-images.githubusercontent.com/110059218/225688433-d0b2b53c-90b6-4481-bc80-f07cf43ee4ef.png)

**One of the installed applications is a file shredder. What is the name of the application? (two words space separated)**

**How many prefetch files were discovered on the system?**

