
# Lab: [Lab Name]: LAB 4 [ File path traversal,traversal sequences stripped with superfluous URL-decode ]

## Vulnerability Type
Directory Traversal (Path Traversal)

## Entry Point
Parameter: ?filename=
- User-controlled file path input

##  Analysis
- Application uses user input to fetch files  
- Input is directly appended to a file path  
- No proper validation or sanitization  
- Basic directory traversal sequences (`../`) are blocked  
- Application performs input decoding but fails to handle double-encoded payloads  

## Payload Used
..%252f..%252f..%252fetc/passwd

## Proof go Concept

![WhatsApp Image 2026-03-31 at 10 09 25](https://github.com/user-attachments/assets/08c1f6c1-b8ed-4047-9a8d-25bfc2826be2)
![WhatsApp Image 2026-03-31 at 10 09 25 (1)](https://github.com/user-attachments/assets/41760eca-7ce0-421b-8965-cb9a38984556)

![WhatsApp Image 2026-03-31 at 10 09 25 (2)](https://github.com/user-attachments/assets/8768a2cd-047e-4a9f-91e5-531f8a237713)
![WhatsApp Image 2026-03-31 at 10 09 25 (2)](https://github.com/user-attachments/assets/184bd9ff-2ca0-4410-9946-c55af9672596)

## Explanation in Words## 
->  I opened the lab and used Burp Suite to intercept the request. I noticed a parameter `?filename=7.jpg` which controls the file being loaded. First, I confirmed the request was working by checking for a 200 OK response. I first tried to directly access `/etc/passwd`, but it didn’t work. Then I attempted path traversal using `../../etc/passwd` and increased it to `../../../../etc/passwd`, but both failed. I also tried bypassing the filter using patterns like `....//....//....//etc/passwd`, but that didn’t work either. This made me think that the application might be decoding the input before processing it. So, I used double encoding by encoding `/` as `%2f` and then encoding it again to `%252f`. Finally, I used the payload `..%252f..%252f..%252fetc/passwd`, which successfully bypassed the filter and allowed me to access sensitive files.
