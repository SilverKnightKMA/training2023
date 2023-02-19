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
xem hướng dẫn bên github thì sẽ có câu lệnh : nc.ps -l port -> port:1348
At what date did the compromise take place?
> hỏi thời gian khởi tạo
![image](https://user-images.githubusercontent.com/110059218/219966755-2c6a32ec-1c11-45db-b3b9-c8d69174d694.png)
