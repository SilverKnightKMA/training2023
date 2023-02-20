# Investigating Windows
Whats the version and year of the windows machine?
![image](https://user-images.githubusercontent.com/110059218/219937708-26278a94-cff9-441c-bdd0-3575e61ae25c.png)
Which user logged in last?
![image](https://user-images.githubusercontent.com/110059218/219937663-6fe0239d-1f17-44eb-b894-c83764bb1ffc.png)
![image](https://user-images.githubusercontent.com/110059218/219937679-ff026929-fc2c-49ad-9a51-f4d35489d338.png)
When did John log onto the system last?
Answer format: MM/DD/YYYY H:MM:SS AM/PM
![image](https://user-images.githubusercontent.com/110059218/219939368-8f42b1c9-b922-4691-a8de-663787ef6ce5.png)
What IP does the system connect to when it first starts?
![image](https://user-images.githubusercontent.com/110059218/219939570-a3d2da84-ce66-4a2a-8b58-55471a919ccc.png)
![image](https://user-images.githubusercontent.com/110059218/219939660-a5707269-73f2-4357-a75d-380ea509e07c.png)
When did Jenny last logon?
![image](https://user-images.githubusercontent.com/110059218/219940791-61d215d2-1a34-45e5-8ec0-2cbad17f3c74.png)
What two accounts had administrative privileges (other than the Administrator user)?
Answer format: username1, username2
![image](https://user-images.githubusercontent.com/110059218/219962849-9576ed59-624d-46c4-92af-ccec44246897.png)
check user thường chỉ có user: jenny có quyền admin vậy câu trả lời sẽ là: jenny, guest.
Whats the name of the scheduled task that is malicous.
![image](https://user-images.githubusercontent.com/110059218/219966057-2158affd-607d-404f-a81b-3d327a445397.png)
![image](https://user-images.githubusercontent.com/110059218/219966075-daf5980a-5967-422d-8fbf-37d0d77b5a33.png)
![image](https://user-images.githubusercontent.com/110059218/219966081-a1609705-cbbb-4f4d-a3ba-0dfa55fd8ab6.png)
có xuất hiện 1 task khá lạ và check trên github thì lại có công dụng khác so với mô tả của task
What file was the task trying to run daily?
* nội dung phần action
What port did this file listen locally for?
xem hướng dẫn bên github thì sẽ có câu lệnh: nc.ps -l port -> port:1348

At what date did the compromise take place?
hỏi thời gian khởi tạo
![image](https://user-images.githubusercontent.com/110059218/219966755-2c6a32ec-1c11-45db-b3b9-c8d69174d694.png)
What tool was used to get Windows passwords?
khi dùng máy ảo cửa sửa của mimikatz cũng hiện liên tục hoặc có thể vào task schedule thấy task có tên gameover dẫn đến thư mục chứa mimimkatz
What was the attackers external control and command servers IP?
![image](https://user-images.githubusercontent.com/110059218/219970757-db78cb44-bcca-428b-8556-56181bcadabc.png)
![image](https://user-images.githubusercontent.com/110059218/219970786-809be824-fd11-4ce1-872c-a9f3130d5109.png)
# Juicy Details
> Reconnaissance
# Matryoshka doll
có hint về việc ẩn dữ liệu trong tấm ảnh nghĩ đến ngay tool binwalk
![image](https://user-images.githubusercontent.com/110059218/220115638-60045569-d7f4-4cef-b033-8831a70ce113.png)
![image](https://user-images.githubusercontent.com/110059218/220115695-f90e0653-869b-431f-84a8-9c9132b36b1a.png)
![image](https://user-images.githubusercontent.com/110059218/220115920-9c1d75bd-a206-4190-afe7-480b5901039f.png)
thực hiện liên tiếp vài lài thì hiện một file ẩn có tên là flag.txt đọc file thu được
![image](https://user-images.githubusercontent.com/110059218/220116105-0ca01147-32e0-4fcb-9ee7-54c3eff26f79.png)
# Glory of the Garden
bài này lúc đầu em nghĩ khó hơn nhưng có vẻ dùng strings | grep là done hint nói về hex editor em lúc đầu nghĩ về việc chỉnh sửa header nhưng có lẽ chỉ đọc strings của ảnh :v
![image](https://user-images.githubusercontent.com/110059218/220116740-5e56b1a7-2dd5-48a1-a727-7da0077f11e6.png)
export object http do em thấy http truyền khá nhiều file
![image](https://user-images.githubusercontent.com/110059218/220117361-133328f5-c649-4fa1-ae9b-4edb6002524e.png)
thu được file có 1 file có tiêu đề khác các file còn lại em thử mở thì thấy đây là 1 dạng mã hóa rất dễ gặp khi gặp dạng bài network là rot13
![image](https://user-images.githubusercontent.com/110059218/220117632-d5e835bc-6cba-4fb4-9bd2-9a7228afc114.png)
![image](https://user-images.githubusercontent.com/110059218/220117749-5950cfa0-1b32-4b4d-adaf-2a75409ebae8.png)
# packet primer
![image](https://user-images.githubusercontent.com/110059218/220118066-f356aad8-1dca-4949-a70c-bb4f7a8b5508.png)
ngay hint đã nói về việc dùng đến analyse để follow stream :v
![image](https://user-images.githubusercontent.com/110059218/220118204-183d1f90-8655-450d-ba9d-c032ec5e7003.png)
![image](https://user-images.githubusercontent.com/110059218/220118503-d6becb01-346c-45e9-9667-06cba629f6d4.png)
flag: picoCTF{p4ck37_5h4rk_01b0a0d6}
# wireshark 2
![image](https://user-images.githubusercontent.com/110059218/220119492-fb88cf48-7d77-4c5b-840c-50398689e669.png)
lúc đầu xuất hiện khá nhiều cờ giả do em k biết đã submit thử
