# emo - hack the box
đầu tiên thực hiện upload file lên hybrid-analysis kết hợp với việc phân tích tĩnh với bộ công cụ oletools
![image](https://user-images.githubusercontent.com/110059218/224494335-a42f2035-8c87-4326-ad12-d8885c5eafe6.png)
khi up lên chúng ta có thể thấy người tấn công cố gắng để chạy powershell

chúng ta cần có 1 tool để decode và tool mình chọn ở đây là [Cyberchef](https://www.youtube.com/watch?v=dQw4w9WgXcQ)
một kỹ thuật thường thấy khi phân tích word tác giả luôn luôn cố gắng làm xáo trộn khiến người đọc khó hiểu nội dung bằng các null bytes và các ký tự được replace có thể phân tích bằng oletools
![image](https://user-images.githubusercontent.com/110059218/224495302-5fe44761-22a6-4d6d-ac71-87726eb3bba5.png)
phần sau có thực hiện việc nối chuỗi theo thứ tự khác nhau nhằm làm khó người phân tích
![image](https://user-images.githubusercontent.com/110059218/224494738-1113d3a9-12cf-4a0e-9e1c-42031d5214bc.png)
đoạn văn bản sau khi decode sơ sơ
![image](https://user-images.githubusercontent.com/110059218/222190320-f64506f7-9184-4fa5-ba65-a7937311139d.png)
![image](https://user-images.githubusercontent.com/110059218/222190444-b4f6981c-2c53-4989-8cbf-d975db69c4be.png)
thực hiện replace và xóa bớt bằng tay bỏ qua một số phần như tạo thư mục hay download xuống
sau đó thực hiện chạy trực tiêp trên powershell
* chú ý đoạn cuối được mã hóa bởi base64 và đã được xor bên trên vì vậy tạm thời bỏ qua một số phần khác và tập trung chính vào những đoạn có liên quan đến chuỗi đó
![image](https://user-images.githubusercontent.com/110059218/222198785-13912241-cbbe-4f16-bec4-a86b1c3c563f.png)
lấy được 1 đoạn bị mã hóa và chúng ta chỉ cần lấy ra và xor 0xdf rồi decode bằng base64
![image](https://user-images.githubusercontent.com/110059218/222198998-eeb68e68-0bc2-4cfe-909f-afd6f45bbcdd.png)
# Illumination
bài này khá giống bài git is good bên ctflearn cần thêm một chút kiến thức về git
nguồn tham khảo: https://git-scm.com/docs
đầu tiên cần xem những lần commit lên bằng câu lệnh git log
![image](https://user-images.githubusercontent.com/110059218/222201792-24d17485-6229-419f-802c-770fe0d9907c.png)
có thấy giữa lần thứ 2 và lấy thứ 3 có xóa 1 thứ gì đó dùng câu lệnh git diff để xem sự thay đổi giữa hai lần commit
![image](https://user-images.githubusercontent.com/110059218/222202027-cef721b4-e765-4a58-8c62-cba5ee78cb05.png)
có 2 đoạn mã base64 chúng ta có thể decode được
![image](https://user-images.githubusercontent.com/110059218/222202249-5060b22b-0ddd-4ff5-98c6-2f86030832e1.png)
# Bucket
**What is the full AWS CLI command used to configure credentials?**
![image](https://user-images.githubusercontent.com/110059218/222204172-bd8660a6-bc26-4cce-a76f-378aa643de71.png)
**What is the 'creation' date of the bucket 'flaws2-logs'?**

search bucket và vào thì có một nhóm được tạo
![image](https://user-images.githubusercontent.com/110059218/222224727-84f3be50-0699-4287-a9f3-9f79ad62e66f.png)
**What is the name of the first generated event -according to time?**

vào thư mục của flaws2-logs và sort theo date tải file tạo đầu tiên để tìm tên
![image](https://user-images.githubusercontent.com/110059218/222225681-20e58358-e159-4147-910a-2269b76fc8d6.png)
**What source IP address generated the event dated 2018-11-28 at 23:03:20 UTC?**

sử dụng 1 tool online để decode file json
![image](https://user-images.githubusercontent.com/110059218/222226583-28e214d5-5f07-491b-ab1c-7e3a1c4e9b0c.png)
đoạn này tải all file về để mò time
![image](https://user-images.githubusercontent.com/110059218/222229446-2dbe240e-7a92-4cbc-bfcd-ad0968157c23.png)
sau một hồi vật lộn thì ra con ip 

**Which IP address does not belong to Amazon AWS infrastructure?**

decode tất cả các file dùng pipe + grep để lấy ra ip 
![image](https://user-images.githubusercontent.com/110059218/222969145-6d29e820-ccbb-442d-ac13-2388294f0056.png)
dùng virustotal tra ip thì ip 104.102.221.250 không thuộc aws

**Which user issued the 'ListBuckets' request?**
![image](https://user-images.githubusercontent.com/110059218/222970600-2824d30d-31cc-4bc2-8a5a-d36aa57e326f.png)
tìm từ khóa ListBuckets và dòng chứa từ khóa với option -n
![image](https://user-images.githubusercontent.com/110059218/222970636-53583469-cb85-43c0-b74f-ccd6f73d31f0.png)
user: level3

**What was the first request issued by the user 'level1'?**
![image](https://user-images.githubusercontent.com/110059218/222970787-683a92ae-3aff-48b7-a01e-0502fe383d01.png)
tìm và xem thời gian sớm nhất
![image](https://user-images.githubusercontent.com/110059218/222971329-ded48b5c-9ebd-4c3d-ae4e-1b793722563b.png)
yêu cầu của user level1 ở đây là creatlogstream

# INTRODUCTION TO CRYPTOHACK
**Question 1**
![image](https://user-images.githubusercontent.com/110059218/222529494-820c3fac-b4f3-48a2-8d44-8ab563365c05.png)
thực hiện chạy file python và thu được flag luôn
![image](https://user-images.githubusercontent.com/110059218/222529585-9494635c-c105-4783-abd2-cbbf20828b97.png)
**Question 2**
![image](https://user-images.githubusercontent.com/110059218/222529667-dea5b081-0cf3-4e18-8aa3-b13d89eb97f1.png)
![image](https://user-images.githubusercontent.com/110059218/222530718-56f06213-3a46-426d-b66f-aad47954b841.png)
in theo chuỗi ra màn hình để lấy flag

**Question 3**
![image](https://user-images.githubusercontent.com/110059218/222531054-6f890af5-d788-427c-b681-50b62336314b.png)
![image](https://user-images.githubusercontent.com/110059218/222531358-34aba2c3-c76f-4dcf-a07f-39d1f743a18b.png)
sử dụng tool decode online để chuyển đổi về dạng ascii

**Question 4**
![image](https://user-images.githubusercontent.com/110059218/222531546-dcc42385-4d7e-4287-bd3e-6c3943018822.png)
như tiêu đề là base64 thì chúng ta dùng base64 để decode và lấy flag 
![image](https://user-images.githubusercontent.com/110059218/222533734-2c00b593-2052-428c-ac1e-2c69d18f40a7.png)

**Question 5**
![image](https://user-images.githubusercontent.com/110059218/222533813-3cbeeba0-c535-416f-bcc9-b178fcb7669c.png)
![image](https://user-images.githubusercontent.com/110059218/222691105-d9ecb4ca-0683-4deb-9713-ae1c2f1a5213.png)
sử dụng thư viện mà đề bài cho để làm
![image](https://user-images.githubusercontent.com/110059218/222691189-ecd8c372-2f1e-4792-b38a-464e640b01b3.png)

**Question 6**
![image](https://user-images.githubusercontent.com/110059218/222658720-f4088c72-bd5f-4ff3-bae6-423a8932858e.png)
![image](https://user-images.githubusercontent.com/110059218/222658776-11a9b2b5-a4be-48c1-8466-bf26850e5bb5.png)
**Question 7**
![image](https://user-images.githubusercontent.com/110059218/222680399-0249da10-806b-4844-93c9-233c87452778.png)
thực hiện xor ngược để ra đoạn flag dạng hex và chuyển về byte
![image](https://user-images.githubusercontent.com/110059218/222680589-7e689a80-cfe8-4b84-9480-941bf80ab39c.png)
![image](https://user-images.githubusercontent.com/110059218/222680234-2297c001-28fc-4a92-b6b9-35a9f82bcae8.png)
**Question 8**
![image](https://user-images.githubusercontent.com/110059218/222680699-cf80e171-d1e8-460c-854e-6ee4cf55531c.png)
![image](https://user-images.githubusercontent.com/110059218/222682117-53811cfb-707d-4e4e-86f1-0ff0e3e5f4ec.png)
sử dụng tool brute-force lấy được flag

**Question 9**
![image](https://user-images.githubusercontent.com/110059218/222682472-c089919e-eba5-4875-8b7d-327f38321e4f.png)
![image](https://user-images.githubusercontent.com/110059218/222688016-7aa85c6a-d1a6-40f1-b692-886b81a34654.png)
![image](https://user-images.githubusercontent.com/110059218/222688123-00c57f41-ae1f-482f-aac7-ba24170ffc45.png)
giải thích sơ về code:
đầu tiên đầu bài có nói nhớ định dạng cờ để có thể decode thì chúng ta có thể thấy cờ sẽ có phần crypto{ và nội dung và }
từ đó ta có thể đoán để tìm ra key để decode
# Obsecure
đoạn code php kẻ tấn công đã cố tình mã hóa để làm khó khăn trong việc đọc code
![image](https://user-images.githubusercontent.com/110059218/223773331-0e2513a1-14e6-4f21-8635-a72d140ecd12.png)
