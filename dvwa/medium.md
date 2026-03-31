##Vulnerability The application directly includes user input without validation.

##Payload Used /etc/passwd

##Explanation

    No sanitization
    Directory traversal allowed
    Leads to Local File Inclusion (LFI)

##Fix

    Use whitelist
    Validate input

##Proof Of Concept 
