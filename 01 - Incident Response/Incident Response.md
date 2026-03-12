
https://tryhackme.com/module/incident-response [No Completado]

![[Pasted image 20260311181340.png]]


NIST incident lifecycle  
Containment  
Eradication  
Recovery  
Chain of custody  
Evidence handling

https://tryhackme.com/room/becomingafirstresponder

![[Pasted image 20260311214930.png]]


https://tryhackme.com/room/introtoirandim

![[Pasted image 20260311214940.png]]

https://tryhackme.com/room/loggingforaccountability

![[Pasted image 20260311214949.png]]

https://tryhackme.com/room/introtologs

![[Pasted image 20260311215003.png]]

https://tryhackme.com/room/splunk101

![[Pasted image 20260311215012.png]]



https://tryhackme.com/room/windowseventlogs


![[Pasted image 20260311215447.png]]

## Elements of a Windows Event Log

Event logs are crucial for troubleshooting any computer incident and help understand the situation and how to remediate the incident. To get this picture well, you must first understand the format in which the information will be presented. Windows offers a standardized means of relaying this system information.

First, we need to know what elements form event logs in Windows systems. These elements are:

- **System Logs:** Records events associated with the Operating System segments. They may include information about hardware changes, device drivers, system changes, and other activities related to the device.
- **Security Logs:** Records events connected to logon and logoff activities on a device. The system's audit policy specifies the events. The logs are an excellent source for analysts to investigate attempted or successful unauthorized activity.
- **Application Logs** :Records events related to applications installed on a system. The main pieces of information include application errors, events, and warnings.
- **Directory Service Events:** Active Directory changes and activities are recorded in these logs, mainly on domain controllers.
- **File Replication Service Events:** Records events associated with Windows Servers during the sharing of Group Policies and logon scripts to domain controllers, from where they may be accessed by the users through the client servers.
- **DNS Event Logs:** DNS servers use these logs to record domain events and to map out
- **Custom Logs:** Events are logged by applications that require custom data storage. This allows applications to control the log size or attach other parameters, such as ACLs, for security purposes.

![[Pasted image 20260311215923.png]]

There are three main ways of accessing these event logs within a Windows system:

1. **Event Viewer** (GUI-based application)
2. **Wevtutil.exe** (command-line tool)
3. **Get-WinEvent** (PowerShell cmdlet)

for the command wevtutil, we should start with /? to access the help feature

using the command [wevtutil el] we can list the log names in the current PC, adding | Measure-Object -Line, we can count the amount of log-name presents, something like categories.

#### Get-WinEvent


Is a PowerShell cmdlet called **Get-WinEvent**. Per Microsoft, the Get-WinEvent cmdlet "gets events from event logs and event tracing log files on local and remote computers." It provides information on event logs and event log providers. Additionally, you can combine numerous events from multiple sources into a single command and filter using XPath queries, structured XML queries, and hash table queries.

**Note**: The **Get-WinEvent** cmdlet replaces the **Get-EventLog** cmdlet.

### Get all logs from a computer

![[Pasted image 20260311223900.png]]

### Get event log providers and log names

![[Pasted image 20260311223919.png]]

### Log filtering

![[Pasted image 20260311223932.png]]

![[Pasted image 20260311224035.png]]

![[Pasted image 20260311224048.png]]


Documentation for Get-WinEvent https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.diagnostics/get-winevent?view=powershell-7.5&viewFallbackFrom=powershell-7.1


USER and EventID query

Get-WinEvent -LogName Security -FilterXPath '*/EventData/Data[@Name="TargetUserName"]="Sam" and */System/EventID=4720'


## Firewall Logs (Windows)

![[Pasted image 20260312174402.png]]

## Cyber Kill Chain
https://tryhackme.com/room/cyberkillchain.

![[Pasted image 20260312174549.png]]


## Cyber Security 101 (Path)

https://tryhackme.com/path/outline/cybersecurity101

![[Pasted image 20260312174609.png]]









## Mitre ATT&CK

https://tryhackme.com/room/mitre

![[Pasted image 20260312174514.png]]

