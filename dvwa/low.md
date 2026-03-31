# DVWA File Inclusion - Low Level

##Vulnerability
The application directly includes user input without validation.

##Payload Used
/etc/passwd

##Explanation
- No sanitization
- Directory traversal allowed
- Leads to Local File Inclusion (LFI)

##Fix
- Use whitelist
- Validate input

##Proof Of Concept
![WhatsApp Image 2026-03-31 at 13 52 37](https://github.com/user-attachments/assets/9a1e8305-fdda-45c5-9d4d-1c97a3897a3a)
![WhatsApp Image 2026-03-31 at 13 52 37 (1)](https://github.com/user-attachments/assets/3c906fce-4095-47e4-ab78-654552b988d3)
