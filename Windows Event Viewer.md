# Log Types Overview

| Log Type | Usage | Example Events |
|--------|------|---------------|
| **System Logs** | The system logs can be helpful in troubleshooting running issues in the OS. These logs provide information on various operating system activities. | - System Startup and Shutdown events<br>- Driver Loading events<br>- System Error events<br>- Hardware events |
| **Security Logs** | Security logs help detect and investigate incidents. These logs provide information on security-related activities in the system. | - Authentication events<br>- Authorization events<br>- Security Policy Change events<br>- User Account Change events<br>- Abnormal Activity events |
| **Application Logs** | Application logs contain events related specifically to an application. Any interactive or non-interactive activity occurring inside the application will be logged here. | - User Interaction events<br>- Application Change events<br>- Application Update events<br>- Application Error events |
| **Audit Logs** | Audit logs provide detailed information about system changes and user activities. They are useful for compliance requirements and security monitoring. | - Data Access events<br>- System Change events<br>- User Activity events<br>- Policy Enforcement events |
| **Network Logs** | Network logs contain information about incoming and outgoing network traffic. They are useful for troubleshooting and incident investigations. | - Incoming Network Traffic events<br>- Outgoing Network Traffic events<br>- Network Connection Logs<br>- Firewall Logs |
| **Access Logs** | Access logs provide detailed information about access to different resources such as web services, databases, and APIs. | - Web Server Access Logs<br>- Database Access Logs<br>- Application Access Logs<br>- API Access Logs |
---
# Windows Security Event IDs

| Event ID | Category | Description |
|--------|----------|-------------|
| **4624** | Authentication | A user account successfully logged in |
| **4625** | Authentication | A user account failed to log in |
| **4634** | Authentication | A user account successfully logged off |
| **4720** | Account Management | A user account was created |
| **4724** | Account Management | An attempt was made to reset an account’s password |
| **4722** | Account Management | A user account was enabled |
| **4725** | Account Management | A user account was disabled |
| **4726** | Account Management | A user account was deleted |
---