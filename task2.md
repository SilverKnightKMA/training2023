# Investigating Windows
**Whats the version and year of the windows machine?**
search computer name registry để lấy đường dẫn trong hkey local machine
![image](https://user-images.githubusercontent.com/110059218/219937708-26278a94-cff9-441c-bdd0-3575e61ae25c.png)
**Which user logged in last?**
![image](https://user-images.githubusercontent.com/110059218/219937663-6fe0239d-1f17-44eb-b894-c83764bb1ffc.png)
![image](https://user-images.githubusercontent.com/110059218/219937679-ff026929-fc2c-49ad-9a51-f4d35489d338.png)
**When did John log onto the system last?**
Answer format: MM/DD/YYYY H:MM:SS AM/PM
![image](https://user-images.githubusercontent.com/110059218/219939368-8f42b1c9-b922-4691-a8de-663787ef6ce5.png)
**What IP does the system connect to when it first starts?**
![image](https://user-images.githubusercontent.com/110059218/219939570-a3d2da84-ce66-4a2a-8b58-55471a919ccc.png)
![image](https://user-images.githubusercontent.com/110059218/219939660-a5707269-73f2-4357-a75d-380ea509e07c.png)
**When did Jenny last logon?**
![image](https://user-images.githubusercontent.com/110059218/219940791-61d215d2-1a34-45e5-8ec0-2cbad17f3c74.png)
**What two accounts had administrative privileges (other than the Administrator user)?
Answer format: username1, username2**
![image](https://user-images.githubusercontent.com/110059218/219962849-9576ed59-624d-46c4-92af-ccec44246897.png)
check user thường chỉ có user: jenny có quyền admin vậy câu trả lời sẽ là: jenny, guest.
**Whats the name of the scheduled task that is malicous.**
![image](https://user-images.githubusercontent.com/110059218/219966057-2158affd-607d-404f-a81b-3d327a445397.png)
![image](https://user-images.githubusercontent.com/110059218/219966075-daf5980a-5967-422d-8fbf-37d0d77b5a33.png)
![image](https://user-images.githubusercontent.com/110059218/219966081-a1609705-cbbb-4f4d-a3ba-0dfa55fd8ab6.png)
có xuất hiện 1 task khá lạ và check trên github thì lại có công dụng khác so với mô tả của task
**What file was the task trying to run daily?**
* nội dung phần action
What port did this file listen locally for?
xem hướng dẫn bên github thì sẽ có câu lệnh: nc.ps -l port -> port:1348

**At what date did the compromise take place?**
hỏi thời gian khởi tạo
![image](https://user-images.githubusercontent.com/110059218/219966755-2c6a32ec-1c11-45db-b3b9-c8d69174d694.png)

**What tool was used to get Windows passwords?**
khi dùng máy ảo cửa sửa của mimikatz cũng hiện liên tục hoặc có thể vào task schedule thấy task có tên gameover dẫn đến thư mục chứa mimimkatz

**What was the attackers external control and command servers IP?**
![image](https://user-images.githubusercontent.com/110059218/219970757-db78cb44-bcca-428b-8556-56181bcadabc.png)
thực hiện mở file host như đường dẫn
![image](https://user-images.githubusercontent.com/110059218/219970786-809be824-fd11-4ce1-872c-a9f3130d5109.png)
![image](https://user-images.githubusercontent.com/110059218/220363662-4bab65d8-bb95-491a-b40d-a494c7886549.png)
khi mở file host ra chúng ta thấy các trang như virustotal,... đều bị chặn khi để ip cục bộ khiến không thể truy cập có lẽ kẻ tấn công không muốn người dùng có thể vào được các trang này, câu trả lời sẽ là: 76.32.97.132

**At what time did Windows first assign special privileges to a new logon?**
thực hiện mở event viewer mở phần security logon special có event id là 4672 thực hiện filter theo id đó và sort theo date
![image](https://user-images.githubusercontent.com/110059218/220365478-e95122c6-cb1a-45bd-99ae-b76b516287d6.png)
search google với keyword: local path for websites in iis path
![image](https://user-images.githubusercontent.com/110059218/220369866-3952411d-b4fc-419d-b7f2-03a468d5c6bb.png)
![image](https://user-images.githubusercontent.com/110059218/220369936-b58c705b-58ab-491a-975a-494f7487128f.png)
file có đuôi jsp
**What was the last port the attacker opened?**
dựa vào hint về firewall chúng ta có thể vào windows firewall để check
If the Windows Firewall is turned off then it will have no effect, and the Inbound and Outbound rules will mean nothing.
Inbound rules: These are to do with other things accessing your computer. If you are running a Web Server on your computer then you will have to tell the Firewall that outsiders are allowed to connect to it.
Outbound rules: These are so that you can let some programs use the Internet, and Block others. You will want to let your Web Browser (Internet Explorer, Firefox, Safari, Chrome, Opera...) have access to the Internet, so you will tell Windows Firewall that it's allowed.
tham khảo một số kiến thức thêm tại: https://superuser.com/questions/48343/what-are-inbound-and-outbound-rules-for-windows-firewall#:~:text=Inbound%20rules%20filter%20traffic%20passing,conditions%20specified%20in%20the%20rule.
![image](https://user-images.githubusercontent.com/110059218/220371495-c940e2c5-6d45-45bc-93a1-be3b68abbfe5.png)
**Check for DNS poisoning, what site was targeted?**
dựa vào việc đổi ip của attacker trong câu trước dễ dàng có thể xác định được tên miền bị tấn công là google.com
# Juicy Details
**Reconnaissance**
mở file và thực hiện đọc lần lượt từ trên xuống dưới để tìm tên tool 
![image](https://user-images.githubusercontent.com/110059218/220645566-552d5584-f68e-4234-a8ef-dc5c6377d30c.png)

***What endpoint was vulnerable to a brute-force attack?***
dễ dàng nghĩ đến việc tấn công brute-force thường nhằm vào password đồng thời hydra cũng là 1 tool brute-force 
![image](https://user-images.githubusercontent.com/110059218/220651478-6b077254-aeba-4ebe-9d29-9cfa3eae61ef.png)

***What endpoint was vulnerable to SQL injection?***
nghĩ ngay đến sqlmap
![image](https://user-images.githubusercontent.com/110059218/220652769-773e858b-8436-476b-8185-8f5f2ad59ca4.png)

***What parameter was used for the SQL injection?***
https://www.geeksforgeeks.org/use-sqlmap-test-website-sql-injection-vulnerability/
tham khảm về tutorial của sqlmap đọc theo thì tham số được sử dụng sẽ là q

***What endpoint did the attacker try to use to retrieve files? (Include the /)***
xuất file thì chắc chắn phải là những hành động cuối cùng nên sẽ đi về cuối log search về tool feroxbuster có tác dụng như ảnh
![image](https://user-images.githubusercontent.com/110059218/220660512-5db35dc4-0b85-45d5-9b9c-fcc908f9a993.png)
tìm được câu trả lời là ftp 

**Stolen data**
***Where can customers usually comment on a shopping website?***
hint: Where can customers usually comment on a shopping website?
nghĩ đến ngay các đường link dẫn đến các sản phẩm xem lại log thì thấy được nmap quét 
![image](https://user-images.githubusercontent.com/110059218/220666735-3e80beea-ae8f-4a10-93fc-1a4675961af8.png)
-> comment đánh giá về sản phẩm : product reviews

***Was their brute-force attack successful? If so, what is the timestamp of the successful login? (Yay/Nay, 11/Apr/2021:09:xx:xx +0000)***
vào log lọc và đọc thông tin về hydra sau một hồi tìm hiểu thì nhưng mã như 401,500,501 là những mã báo lỗi còn mã 200 831 là báo thành công
![image](https://user-images.githubusercontent.com/110059218/220693619-93f68a61-47b7-4eda-9d0f-b3d861fe80f8.png)

***What user information was the attacker able to retrieve from the endpoint vulnerable to SQL injection?***
![image](https://user-images.githubusercontent.com/110059218/220695922-5e5020be-0376-4941-ac19-cc5de19e7820.png)
như ở câu đầu tiên về việc lấy email thì hacker thực hiện việc tải xuống qua lệnh curl

***What files did they try to download from the vulnerable endpoint? (endpoint from the previous task, question #5)***
câu này chỉ cần lấy tên file ở đuôi câu 5 phần trước
![image](https://user-images.githubusercontent.com/110059218/220696666-8409fb97-673c-4931-8f32-2ff3e409fb5f.png)

***What service and account name were used to retrieve files from the previous question? (service, username)***
dựa vào vài câu hỏi bên trên thì có thể trả lời service: ftp còn user vào check file vsftpd.log(là file log ghi lại quá trình đăng nhập)
tên đăng nhập là anon nhưng khi submit lại báo sai thì tên anon này liên tưởng đến nhóm hacker mũ đen anonymous và cái tên này cũng có nghĩa  là vô danh
![image](https://user-images.githubusercontent.com/110059218/220699562-09afd29e-c096-4aa3-832d-e5a13787ef43.png)

***What service and username were used to gain shell access to the server? (service, username)***
em thực hiện search về tác dụng của các file log thì có search ra 1 file log liên quan đến việc xác thực tài khoản
https://www.bkns.vn/cac-file-log-quan-trong-tren-linux.html#:~:text=File%20log%20%2Fvar%2Flog%2Fauth.log&text=Ch%E1%BB%A9a%20th%C3%B4ng%20tin%20x%C3%A1c%20th%E1%BB%B1c,ki%E1%BA%BFm%20trong%20file%20log%20n%C3%A0y.
![image](https://user-images.githubusercontent.com/110059218/220699985-b17e2c3a-7d97-429e-a56f-3d53da3ed97f.png)
khi vào auth.log dễ dàng nhận ra service mà hacker dùng chính là ssh và tấn công brute-force 
![image](https://user-images.githubusercontent.com/110059218/220700272-f45afd1f-341c-46be-8618-3597aca0a7c2.png)
username:www-data
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
# wireshark doo doo
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
chú ý những lần gửi cờ giả đều đến từ dst giống nhau dựa vài đó có thể lọc ra
để ý thì dns gửi những chuỗi kí tự ghép lại giống base64:cGljb0NURntkbnNfM3hmMWxfZnR3X2RlYWRiZWVmfQ==
decode ta thu được cờ
![image](https://user-images.githubusercontent.com/110059218/221247759-47881be1-82fa-489d-839b-55b468b7bf1a.png)
# Trivial Flag Transfer Protocol
![image](https://user-images.githubusercontent.com/110059218/221250346-68c34a6a-1083-4d26-a204-188ea84f733e.png)
khi mới mở file bằng wireshark có thể thấy đã có gói được đẩy lên
export object tftp để lấy các gói dữ liệu đã gửi
![image](https://user-images.githubusercontent.com/110059218/221251349-ecf44a95-fab4-40f4-8eaf-ef9c8b3db962.png)
giải mã rot13 và cắt chuỗi cho hợp lý được thông điệp(file instructions.txt)
![image](https://user-images.githubusercontent.com/110059218/221250179-ac8d4f82-cff3-41ff-bf55-b12c0fd93d25.png)
![image](https://user-images.githubusercontent.com/110059218/221251203-7fda12c3-e91c-4249-8d7d-29eb4f71d346.png)
thông điệp thứ 2 từ file plan
từ đó ta thực hiện stego các ảnh 
![image](https://user-images.githubusercontent.com/110059218/221254714-2bda4886-07ea-4a4b-9bb9-0eb6782082dd.png)
giải nén file deb xem bên trong có gì 
![image](https://user-images.githubusercontent.com/110059218/221255121-ec7ebb66-8fae-4d21-91f7-6807ec4df055.png)
các file đều chỉ dẫn tới 1 tool có thể mã hóa tệp khác trong ảnh là steghide
dùng steghide với cả 3 hình và mật khẩu tác giả có để trong plan là DUEDILIGENCE
![image](https://user-images.githubusercontent.com/110059218/221255923-e41683c8-e0df-4605-9a84-736664ee819f.png)
![image](https://user-images.githubusercontent.com/110059218/221257064-f3949903-3d78-4b41-b817-3a4fa1977cc3.png)
# Carnage
**What was the date and time for the first HTTP connection to the malicious IP?**
thực hiện lọc luồng http lấy time đầu tiên được kết nối
![image](https://user-images.githubusercontent.com/110059218/221173634-aeceba0c-262d-427a-8c66-dda3fffeee52.png)
**What is the name of the zip file that was downloaded?**
![image](https://user-images.githubusercontent.com/110059218/221173689-c6db0e9e-eef4-44a4-98e1-635c37221c18.png)
đọc cột info để lấy thông tin tệp tải xuống
**What was the domain hosting the malicious zip file?**
thực hiện follow http stream
![image](https://user-images.githubusercontent.com/110059218/221173863-208c2df5-c388-421d-9f0a-5cddf4710538.png)
**What is the name of the webserver of the malicious IP from which the zip file was downloaded?**
![image](https://user-images.githubusercontent.com/110059218/221174035-319f00a0-796a-4155-94b2-e00249d5ffdd.png)
phần dưới có hiển thị phần file trong file zip được tải xuống ở luồng 
**What is the version of the webserver from the previous question?**
![image](https://user-images.githubusercontent.com/110059218/221174136-bb2583d0-ba97-4493-8558-0ce9eb35e7cf.png)
phần x-powered-by thể hiện cho version của webserver
**Malicious files were downloaded to the victim host from multiple domains. What were the three domains involved with this activity?**
đọc sơ qua 1 số bài về https cộng với trong file thì cho thấy port mà SSL/TLS kết nối đến là 443
![image](https://user-images.githubusercontent.com/110059218/221183825-69ee819a-fbd1-4c11-a463-20cffa8121f2.png)
dựa vào hint đầu bài cho tìm từ giây thứ 11 đến giây thứ 30 sẽ có 3 source khác nhau
**Which certificate authority issued the SSL certificate to the first domain from the previous question?**
follow tcp stream của source đầu tiên để lấy thông tin về nơi cấp cert
![image](https://user-images.githubusercontent.com/110059218/221184236-eddce33a-b7fa-4dd1-a7e4-8d2ff18a93ea.png)
**What are the two IP addresses of the Cobalt Strike servers? Use VirusTotal (the Community tab) to confirm if IPs are identified as Cobalt Strike C2 servers. (answer format: enter the IP addresses in sequential order)**
http thường được lưu ở cổng 8080 và 80 chọn statistíc -> conversation
lọc packet truyền nhiều nhất ở port 8080 và 80
![image](https://user-images.githubusercontent.com/110059218/221217539-84192e99-0ad6-4f84-9715-1240c0269b4f.png)
![image](https://user-images.githubusercontent.com/110059218/221218412-bba9f1d6-1376-416e-aba1-bd812ffd09d3.png)
**What is the Host header for the first Cobalt Strike IP address from the previous question?**
filter ip.addr == 185.106.96.158
follow tcp stream lấy tên host
![image](https://user-images.githubusercontent.com/110059218/221220998-8f453140-3dea-4d82-baa2-5a255ec39c36.png)
**What is the domain name for the first IP address of the Cobalt Strike server? You may use VirusTotal to confirm if it's the Cobalt Strike server (check the Community tab).**
lên virustotal và search ip của câu trên
![image](https://user-images.githubusercontent.com/110059218/221219098-4d2c8362-a9b8-463a-992b-42364963a3a5.png)
**What is the domain name of the second Cobalt Strike server IP?  You may use VirusTotal to confirm if it's the Cobalt Strike server (check the Community tab).**
![image](https://user-images.githubusercontent.com/110059218/221222027-96b8366b-4de4-4497-bc7f-1c27cdeb9e9a.png)
**What is the domain name of the post-infection traffic?**
thực hiện filter POST
![image](https://user-images.githubusercontent.com/110059218/221225451-a86bf509-8da0-4db0-9f00-351498cff23a.png)
tên source là tên câu trả lời 
**What are the first eleven characters that the victim host sends out to the malicious domain involved in the post-infection traffic?**
phần info lấy 11 chữ cái đầu
![image](https://user-images.githubusercontent.com/110059218/221225892-ff1f7655-995c-4adb-a2a5-6de199f97eec.png)
**What was the length for the first packet sent out to the C2 server?**
length là phần độ dài của gói tin
![image](https://user-images.githubusercontent.com/110059218/221226423-97afaa0b-9dc4-4eec-b0ad-2b18c70becf6.png)

**What was the Server header for the malicious domain from the previous question?**
![image](https://user-images.githubusercontent.com/110059218/221227196-8e702285-77c0-4c97-b006-69b3782db1f6.png)
follow http stream lấy tên server
![image](https://user-images.githubusercontent.com/110059218/221227441-e1d4d47f-b670-4628-9115-32cea484642d.png)
**The malware used an API to check for the IP address of the victim’s machine. What was the date and time when the DNS query for the IP check domain occurred? (answer format: yyyy-mm-dd hh:mm:ss UTC)**
![image](https://user-images.githubusercontent.com/110059218/221241996-f97317df-0b77-4050-b4c8-a440a28f0b31.png)
filter api rồi nhập các time đầu tiên kết nối tới mà malware sử dụng search thử thì có 1 api liên quan đến malware
**What was the domain in the DNS query from the previous question?**
lấy tên domain từ câu trước nhập vào
**Looks like there was some malicious spam (malspam) activity going on. What was the first MAIL FROM address observed in the traffic?**
search trên mạng về giao thức của email là smtp,pop,imap
filter các giao thức trên với contains MAIL FROM và lấy mail đầu tiên
![image](https://user-images.githubusercontent.com/110059218/221244594-a9fd538b-e743-4a56-9e25-111ef70f6621.png)
**How many packets were observed for the SMTP traffic?**
vào statistics chọn protocol hierarchy
![image](https://user-images.githubusercontent.com/110059218/221245389-1c82ce7e-bdef-4576-bfc1-28128394cd88.png)
![image](https://user-images.githubusercontent.com/110059218/221245279-75229256-f6a5-4f4c-862a-d8cd9f2654e6.png)
số packet là 1439
# What Lies Within
![image](https://user-images.githubusercontent.com/110059218/221367339-9de55f80-344e-41ac-bb1b-134d9651f8f7.png)
dùng tool stego online decode ra flag
# Squidgame
***Attacker1***
đầu tiên chúng ta dùng oletools 1 công cụ để phân tích các file word
![image](https://user-images.githubusercontent.com/110059218/221367479-ffab62e4-5d6e-4422-8d61-da7a493d0e91.png)
sau khi phân tích thì có thể đọc documents để biết thêm về cách thức ẩn dữ liệu 
![image](https://user-images.githubusercontent.com/110059218/221367550-873ea5aa-3c69-43e4-8652-2a56522c53de.png)
đa số là các phép cộng các chuỗi nhưng có 1 đoạn replace mà chúng ta cần để ý
![image](https://user-images.githubusercontent.com/110059218/221367601-869397ad-b253-48ce-8ebc-920bb7d20598.png)
mở ở phần 4 có 1 đoạn chuỗi khớp với thuật toán mã hóa bên trên
![image](https://user-images.githubusercontent.com/110059218/221367740-9d20796e-3819-4cdd-ad86-a2cbaa5aefb2.png)
kết quả sau khi decode
![image](https://user-images.githubusercontent.com/110059218/221367984-6977c7c0-2aa3-4d34-9c94-2bdce0d9fc78.png)
**What is the malicious C2 domain you found in the maldoc where an executable download was attempted?**
http://fpetraardella.band/xap_102b-AZ1/704e.php?l=litten4.gas
![image](https://user-images.githubusercontent.com/110059218/221368098-1e849675-1969-4d14-9deb-eee9fce5f2b6.png)
**What executable file is the maldoc trying to drop?**
![image](https://user-images.githubusercontent.com/110059218/221368122-f60ba5c3-fc3a-4bd8-a67a-ab3d75b158a3.png)
![image](https://user-images.githubusercontent.com/110059218/221368261-292fbbd7-4e29-4820-8b4e-895c67943b0f.png)
**In what folder is it dropping the malicious executable? (hint: %Folder%)**
câu này có 1 đoạn liên quan đến path
search thì thấy folder là 
![image](https://user-images.githubusercontent.com/110059218/221368414-fbf62cde-6789-4db1-9f38-ca777f9fc3b9.png)
**Provide the name of the COM object the maldoc is trying to access.**

gợi ý check trường clsid
![image](https://user-images.githubusercontent.com/110059218/221368466-8b9e0e99-8a1c-48f6-92e1-4c2ebfa3ecff.png)
search google về id thì ra kết quả là
![image](https://user-images.githubusercontent.com/110059218/221368530-dc114d1f-a9f6-4df8-bbf5-b66b47ad9e74.png)
**Include the malicious IP and the php extension found in the maldoc. (Format: IP/name.php)**
câu này thì hiện khá rõ ràng 
![image](https://user-images.githubusercontent.com/110059218/221368572-305ea32b-2ca1-4ca8-b77a-b4092e8d7c0d.png)
**Find the phone number in the maldoc. (Answer format: xxx-xxx-xxxx)**
check meta file thì có hiện số điện thoại của author
![image](https://user-images.githubusercontent.com/110059218/221368645-3073c72f-e0e4-45dc-8df1-6f2319aaa12b.png)
**Doing some static analysis, provide the type of maldoc this is under the keyword “AutoOpen”.**
![image](https://user-images.githubusercontent.com/110059218/221368725-95d83cf7-99cc-414d-988f-7d8166f5beb5.png)
một công cụ khác trong oletool
![image](https://user-images.githubusercontent.com/110059218/221368791-817ad3de-c3e2-41dc-be6f-6ef490bd0188.png)
dùng tool + pipe + grep để ra đáp án

**Provide the subject for this maldoc. (make sure to remove the extra whitespace)**
subject lấy từ phần check file của câu phone number 
![image](https://user-images.githubusercontent.com/110059218/221368964-b4e60447-18cf-4919-9847-ac5c86c0d8be.png)

**Provide the time when this document was last saved. (Format: YEAR-MONTH-DAY XX:XX:XX)**
hint : Use oletimes
![image](https://user-images.githubusercontent.com/110059218/221369026-bc58b0ed-3b67-4565-a51d-071df34df295.png)

**Provide the stream number that contains a macro.**
![image](https://user-images.githubusercontent.com/110059218/221369122-a019c596-601a-494e-ab05-f2acb8dfca88.png)
stream 8 có contains Macro

**Provide the name of the stream that contains a macro.**
name:ThisDocuments

***Attacker2***
**Provide the streams (numbers) that contain macros.**
![image](https://user-images.githubusercontent.com/110059218/221369507-797ab01c-3a06-4c4a-bbd9-2fb53add695f.png)
có 4 luồng đang chứa macro
**Provide the size (bytes) of the compiled code for the second stream that contains a macro.**
lấy đáp án từ ảnh của câu trên: 13867
**Provide the largest number of bytes found while analyzing the streams.**
lấy số lớn nhất ở cột thứ 2: 63641
**Find the command located in the ‘fun’ field ( make sure to reverse the string).**
dùng olevba phân tích thì vô tình đọc được 1 đoạn shell được rev
![image](https://user-images.githubusercontent.com/110059218/221369976-93310546-090b-4e6a-af79-b1cb2c244c3f.png)
**Provide the first domain found in the maldoc.**
![image](https://user-images.githubusercontent.com/110059218/221370105-4b2edf9b-75a3-4ea1-9fe4-0e6d802fd313.png)
**Provide the second domain found in the maldoc.**
2 câu lấy lần lượt các url mà attacker đã cố gắng tải các tệp dll độc hại
**Provide the name of the first malicious DLL it retrieves from the C2 server.**
xem path đầu tiên sẽ thấy tên dll được tải xuống đầu tiên: www1.dll
![image](https://user-images.githubusercontent.com/110059218/221370316-101a511e-3fa0-439e-afb3-5edff80e274e.png)
**How many DLLs does the maldoc retrieve from the domains?**:5
**Provide the path of where the malicious DLLs are getting dropped onto?**
path ở ổ C ảnh trên

**What program is it using to run DLLs?**
![image](https://user-images.githubusercontent.com/110059218/221370389-36b525d4-583f-4883-829e-6500f840bf3f.png)
**How many seconds does the function in the maldoc sleep for to fully execute the malicious DLLs?**:15 quy đổi về giây như thời gian ở trên ảnh
**Under what stream did the main malicious script use to retrieve DLLs from the C2 domains? (Provide the name of the stream).**
![image](https://user-images.githubusercontent.com/110059218/221370538-032d3e64-c203-44e1-b794-2699398a36f1.png)
thấy được olestream
***attacker2***
**Provide the executable name being downloaded.**
![image](https://user-images.githubusercontent.com/110059218/221370631-a96fda35-76bb-4038-bf20-58f12d709fec.png)
dùng tool olevba để phân tích
**What program is used to run the executable?**
![image](https://user-images.githubusercontent.com/110059218/221371614-6c34784c-e480-4ab6-b99d-e8c29852c36d.png)
**Provide the malicious URI included in the maldoc that was used to download the binary (without http/https).**
sử dụng 1 tool khác để phân tích là viper monkey
![image](https://user-images.githubusercontent.com/110059218/221372548-1b0e1f25-5dbe-463f-8aa2-a7c205ba1deb.png)
**What folder does the binary gets dropped in?**
ProgramData hỏi về thư mục chứa file binary
![image](https://user-images.githubusercontent.com/110059218/221372720-aedc1769-7238-4035-b1b8-ba8fbac3fde3.png)
**Which stream executes the binary that was downloaded?**
dễ dàng có thể thấy tên stream tải xuông file là: VBA/T -> A3
***Attacker 4***
**Provide the first decoded string found in this maldoc.**
![image](https://user-images.githubusercontent.com/110059218/221376081-af34e90d-6844-466e-a075-400589f0424f.png)
có gợi ý đến phép xor bit
![image](https://user-images.githubusercontent.com/110059218/221376106-79102260-235f-4dd4-aa76-4120e2321b11.png)
ra kết quả như trong ảnh

**Provide the name of the binary being dropped.**
![image](https://user-images.githubusercontent.com/110059218/221376249-58fa1b15-232d-41ae-9d7c-0be0d5e15b45.png)
hint có nói đến việc unxor thì em ném hết vào decode submit thì có 1 kết quả đúng 
![image](https://user-images.githubusercontent.com/110059218/221376480-3510d679-996c-421c-9aec-285f13cfbefc.png)
**Provide the folder where the binary is being dropped to.**
decode phần open
![image](https://user-images.githubusercontent.com/110059218/221376562-83a27030-ed92-41f6-ad55-286ab2e416bd.png)
![image](https://user-images.githubusercontent.com/110059218/221377368-388ea146-ff80-4f1e-901b-590545d8cc31.png)
**Provide the full URI from which the second binary was downloaded (exclude http/https).**
end function 1 thì tiếp đến sẽ là thời gian download malware thứ 2
![image](https://user-images.githubusercontent.com/110059218/221376797-bd09daae-96cb-4042-9845-37652a15e2f3.png)
![image](https://user-images.githubusercontent.com/110059218/221376830-b118adac-1e5b-4126-8353-3e42ffcc68ca.png)
**Provide the name of the second binary.**
bin.exe (đoạn cuối của đường link tải file malware)
***Attacker 5***
**What is the caption you found in the maldoc?**
![image](https://user-images.githubusercontent.com/110059218/221377688-f643f98f-631e-491b-9676-148607859a6f.png)
dùng oletools check từng cái một
