##Vulnerability The application directly includes user input without validation.

##Payload Used
/etc/passwd

##Explanation
No sanitization
Directory traversal allowed
Leads to Local File Inclusion (LFI)

##Fix
Use whitelist
Validate input

##Proof Of Concept 
![WhatsApp Image 2026-03-31 at 14 05 53 (1)](https://github.com/user-attachments/assets/21761987-5a51-41f0-851c-a5d49553cde0)
