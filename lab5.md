# Lab: [Lab Name]: LAB 5 [ File path traversal,validation of start of path ]

## Vulnerability Type
Directory Traversal (Path Traversal)

## Entry Point
Parameter: ?filename=
- User-controlled file path input

###  Analysis
- Application uses user input to fetch files  
- Input is directly appended to a file path  
- Application validates the start of the path (e.g. `/var/www/images`)  
- Validation is incomplete and can be bypassed  
- Directory traversal sequences (`../`) can be used after the valid path  

## Payload Used
/var/www/images/../../../etc/passwd

## Proof go Concept

![WhatsApp Image 2026-03-31 at 10 31 08](https://github.com/user-attachments/assets/db262971-51a4-4630-9620-25cba2ae51b9)
![WhatsApp Image 2026-03-31 at 10 31 08 (1)](https://github.com/user-attachments/assets/bd2b39e9-9276-4183-aba2-23e2ad82a541)
![WhatsApp Image 2026-03-31 at 10 31 08 (2)](https://github.com/user-attachments/assets/63b8f7a8-5ea9-4226-a18a-024b8f3d2209)


## Explanation in Words## 
--> I opened the lab and intercepted the request using Burp Suite. I noticed the application was using a file path and the lab instructions mentioned validation of the start of the path. From this, I understood that the application checks whether the path begins with a specific directory (e.g. `/var/www/images`). So instead of removing the path completely, I kept the valid starting path and injected my payload after it. I used `/var/www/images/../../../etc/passwd`, which allowed me to traverse خارج the intended directory while still passing the initial validation check. As a result, I was able to access the sensitive `/etc/passwd` file.
