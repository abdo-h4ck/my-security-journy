# Inconsistent Security Controls (Privilege Escalation)

## Description
The application allows users to update their email address without verifying if the user belongs to the organization. By changing the email to an internal company domain, the user is granted administrative privileges.

## Steps to Reproduce
1. Registered a new account with any email.
2. Logged in and navigated to the "My Account" page.
3. Changed the email address to `admin@dontwannacry.com` (a company domain).
4. The application accepted the new email without requiring verification.
5. The "Admin Panel" link appeared in the navigation bar.
6. Accessed the Admin Panel and deleted the user `carlos`.

## Remediation
The server must verify the user's identity and role before granting administrative access. Changing an email to a privileged domain should not automatically grant admin rights without proper authorization.
