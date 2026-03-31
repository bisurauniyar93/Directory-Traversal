
# Lab: [Lab Name]: LAB 3 [ File path traversal,traversal sequences stripped non-recursively ]

## Vulnerability Type
Directory Traversal (Path Traversal)

## Entry Point
Parameter: ?filename=
- User-controlled file path input

## Analysis
- Application uses user input to fetch files  
- Input is directly appended to a file path  
- No proper validation or sanitization  
- Basic directory traversal sequences (`../`) are blocked  
- Application fails to properly filter alternative traversal patterns (e.g. `....//`)  

## Payload Used
....//....//....//etc/passwd

## Proof go Concept
![WhatsApp Image 2026-03-31 at 09 25 50](https://github.com/user-attachments/assets/a2d262ea-f822-4c1e-bdde-de4d269f4ccb)

![WhatsApp Image 2026-03-31 at 09 25 50 (1)](https://github.com/user-attachments/assets/117a3c98-211a-40d7-b219-90d6ed2ff8b9)

![WhatsApp Image 2026-03-31 at 09 25 50 (2)](https://github.com/user-attachments/assets/b0744c34-92a4-414f-ae09-7bbdf17db4f3)

![WhatsApp Image 2026-03-31 at 09 25 50 (3)](https://github.com/user-attachments/assets/264cc7af-2146-4cb2-ad61-737e636845cc)

![WhatsApp Image 2026-03-31 at 09 25 50 (4)](https://github.com/user-attachments/assets/056a4b5e-c9c7-4b08-ac76-7fe6ab3b3036)

![WhatsApp Image 2026-03-31 at 09 25 50 (5)](https://github.com/user-attachments/assets/e1d94f05-05c1-407e-866f-76ebe20b6334)

![WhatsApp Image 2026-03-31 at 09 25 50 (6)](https://github.com/user-attachments/assets/891507b3-6fff-4d5c-9223-c27c5bf3b4a0)

![WhatsApp Image 2026-03-31 at 09 25 50 (7)](https://github.com/user-attachments/assets/c96578ba-631a-462b-98a1-d4fb704af02d)

![WhatsApp Image 2026-03-31 at 09 25 50 (8)](https://github.com/user-attachments/assets/df051090-ac92-4531-91cd-2bf8a5555c8f)

## Explanation in Words## 
->  I opened the lab and used Burp Suite to intercept the request. I noticed a parameter `?filename=7.jpg` which controls the file being loaded. First, I confirmed the request was working by checking for a 200 OK response. Then I tried to access a sensitive file by changing it to `/etc/passwd`, but it didn’t work. Then I attempted path traversal using `../../etc/passwd` and later increased it to `../../../../etc/passwd`, but both failed. This made me realize that the application is filtering or blocking normal traversal sequences like `../`. To bypass this filter, I modified the payload and used `....//....//....//etc/passwd`. This worked because the filter did not properly handle this pattern, and the server interpreted it as valid traversal. As a result, I was able to access sensitive files outside the intended directory.
