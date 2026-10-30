# Weak Isolation on Dual-Use Endpoint (Privilege Escalation)

## Description
The application's password change functionality did not properly verify the user's current password when the `current-password` parameter was omitted. Additionally, the `username` parameter was trusted from the request body, allowing an attacker to change the password of another user (administrator).

## Steps to Reproduce
1. Logged in as `wiener:peter`.
2. Navigated to the "Change password" page.
3. Intercepted the request in Burp Suite.
4. Removed the `current-password` parameter from the request body.
5. Changed the `username` parameter to `administrator`.
6. Set a new password for the administrator account.
7. Logged out, and logged in as `administrator` with the new password.
8. Accessed the Admin Panel and deleted the user `carlos`.

## Remediation
The server must always require and verify the current password before allowing a password change. Additionally, the user identity should be derived from the session, not from user-supplied parameters.
