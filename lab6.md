# Lab: [Lab Name]: LAB 6 [ File path traversal,validation of file extension with null byte bypass ]

## Vulnerability Type
Directory Traversal (Path Traversal)

## Entry Point
Parameter: ?filename=
- User-controlled file path input

##Analysis
- Application uses user input to fetch files  
- Input is directly appended to a file path  
- Application validates file extension (e.g. `.jpg`, `.png`)  
- Validation is incomplete and can be bypassed using a null byte (`%00`)  
- Directory traversal sequences (`../`) are used before the null byte  

## Payload Used
../../../etc/passwd%00.jpg

## Proof go Concept
![WhatsApp Image 2026-03-31 at 10 49 13](https://github.com/user-attachments/assets/9f8f301c-1209-4f4e-84d0-712edf1ab02d)

![WhatsApp Image 2026-03-31 at 10 49 13 (1)](https://github.com/user-attachments/assets/2c9dca30-19ab-4614-bd9e-40bbab9956f4)

## Explanation in Words## 
->  I opened the lab and used Burp Suite to intercept the request. I noticed a parameter `?filename=7.jpg` which controls the file being loaded. First, I confirmed the request was working by checking for a 200 OK response.
Before trying different payloads, I read the lab instructions and noticed that the application validates the file extension with null bytes. I learned that this can sometimes be bypassed using a null byte. A null byte (`%00`) acts as a string terminator in some systems, meaning anything after it may be ignored. The application expects files like `.jpg` or `.png`, so I kept the extension but injected my payload before it. I used `../../../etc/passwd%00.jpg`, where `%00` causes the server to treat the filename as `../../../etc/passwd` while still passing the extension check. As a result, I was able to access the sensitive file successfully.

