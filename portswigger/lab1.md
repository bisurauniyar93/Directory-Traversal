# Lab: [Lab Name]: LAB 1 [ File path traversal,simple case ]

## Vulnerability Type
Directory Traversal (Path Traversal)

## Entry Point
Parameter: ?filename=
- User-controlled file path input

## Analysis
- Application uses user input to fetch files
- Input is directly appended to a file path
- No proper validation or Sanitization
- Allow Directory Traversal Sequences ('../')

## Payload Used
../../../../etc/passwd

## Proof go Concept
![WhatsApp Image 2026-03-31 at 08 42 17](https://github.com/user-attachments/assets/6700f23e-99f5-44b9-9fa4-aea2609b528a)

![WhatsApp Image 2026-03-31 at 08 42 17 (1)](https://github.com/user-attachments/assets/f498d19f-549e-403e-9aae-708ee4687f7d)

![WhatsApp Image 2026-03-31 at 08 42 17 (2)](https://github.com/user-attachments/assets/45ac799e-29e3-4ec2-83f7-0823e6d51f31)
![WhatsApp Image 2026-03-31 at 08 44 17](https://github.com/user-attachments/assets/7c2b5000-64a3-4170-950b-c0a9857164b7)


## Explanation in Words## 
->  I opened the lab and used Burp Suite to intercept the request. I noticed a parameter `?filename=7.jpg` which controls the file being loaded. First, I confirmed the request was working by checking for a 200 OK response. Then I tried to directly access a sensitive file by changing the value to `/etc/passwd`, but it didn’t work. I realized the application might be restricting direct access, so I tried using path traversal. I started with `../../etc/passwd`, but it was not enough. Then I increased the traversal depth step by step, and finally `../../../../etc/passwd` worked. This allowed me to access sensitive files outside the intended directory.. 
