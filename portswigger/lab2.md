
# Lab: [Lab Name]: LAB 2 [ File path traversal,traversal sequence blocked with absolute path bypass ]

## Vulnerability Type
Directory Traversal (Path Traversal)

## Entry Point
Parameter: ?filename=
- User-controlled file path input

## Analysis
- Application uses user input to fetch files  
- Input is directly appended to a file path  
- No proper validation or sanitization  
- Directory traversal sequences (`../`) are blocked  
- Application fails to block absolute paths (e.g. `/etc/passwd`)
  
## Payload Used
/etc/passwd

## Proof go Concept

![WhatsApp Image 2026-03-31 at 09 05 39 (4)](https://github.com/user-attachments/assets/97d6ca3e-3a4c-42a1-8199-8336d495fb90)


![WhatsApp Image 2026-03-31 at 09 05 39 (5)](https://github.com/user-attachments/assets/7c2465a8-ab58-4516-93ab-09ca5c34c639)

![WhatsApp Image 2026-03-31 at 09 05 39 (6)](https://github.com/user-attachments/assets/e624f686-be5e-4219-9326-bc8719bace8d)


![WhatsApp Image 2026-03-31 at 09 05 39 (7)](https://github.com/user-attachments/assets/7013be29-cc1a-4b85-9362-a6183c115ffc)


![WhatsApp Image 2026-03-31 at 09 05 39 (8)](https://github.com/user-attachments/assets/16c036f4-87d6-4c9f-b1e1-db38955e64d4)


## Explanation in Words## 
->  I opened the lab and used Burp Suite to intercept the request. I noticed a parameter `?filename=47.jpg` which controls the file being loaded. First, I confirmed the request was working by checking for a 200 OK response. I tried to directly access a sensitive file by changing the value to `/etc/passwd`, and it worked. This showed that the application allows absolute paths. I realized that using path traversal sequences like `../../` was not needed in this case because the filter blocks traversal patterns but fails to block absolute paths. As a result, I was able to access sensitive files directly.
