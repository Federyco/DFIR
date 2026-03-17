
- https://tryhackme.com/module/incident-response [No Completado]

![[Pasted image 20260311181340.png]]


NIST incident lifecycle  
Containment  
Eradication  
Recovery  
Chain of custody  
Evidence handling

- https://tryhackme.com/room/becomingafirstresponder [Completado]
 
![[Pasted image 20260311214930.png]]



![[Pasted image 20260314021422.png]]

![[Pasted image 20260314021741.png]]
[Guideline for Evidence Collection and Archiving](https://datatracker.ietf.org/doc/html/rfc3227#section-2.1)

![[Pasted image 20260314021823.png]]
![[Pasted image 20260314021834.png]]
![[Pasted image 20260314021844.png]]

![[Pasted image 20260314022013.png]]
![[Pasted image 20260314022020.png]]
![[Pasted image 20260314022037.png]]
![[Pasted image 20260314022104.png]]
![[Pasted image 20260314022154.png]]

![[Pasted image 20260314022305.png]]
![[Pasted image 20260314022313.png]]

![[Pasted image 20260314111755.png]]
![[Pasted image 20260314111801.png]]

![[Pasted image 20260314111920.png]]
![[Pasted image 20260314111940.png]]
![[Pasted image 20260314111950.png]]


















- https://tryhackme.com/room/introtoirandim [Completado]


![[Pasted image 20260311214940.png]]

![[Pasted image 20260314015219.png]]

![[Pasted image 20260314015230.png]]

![[Pasted image 20260314015242.png]]

![[Pasted image 20260314015252.png]]

![[Pasted image 20260314015259.png]]

![[Pasted image 20260314020230.png]]
![[Pasted image 20260314020245.png]]

![[Pasted image 20260314020728.png]]

![[Pasted image 20260314020738.png]]
![[Pasted image 20260314020752.png]]





- https://tryhackme.com/room/loggingforaccountability [Completado]

![[Pasted image 20260311214949.png]]

![[Pasted image 20260314010235.png]]

[STRIDE CHART](https://www.microsoft.com/en-us/security/blog/2007/09/11/stride-chart/)





- https://tryhackme.com/room/auditingandmonitoringse [No Completado]

![[Pasted image 20260314010514.png]]

- https://tryhackme.com/room/iaaaidm [No Completado]

![[Pasted image 20260314010606.png]]

- https://tryhackme.com/room/securityprinciples [No Completado]

![[Pasted image 20260314010640.png]]



- https://tryhackme.com/room/introtologs [Completado]

![[Pasted image 20260311215003.png]]


![[Pasted image 20260313170138.png]]

![[Pasted image 20260313170201.png]]

Example:
![[Pasted image 20260313170214.png]]

se pueden crear archivos de rsyslogs basados en configuraciones, para este ejemplo se utilizará el servicio ssh

![[Pasted image 20260313175633.png]]

![[Pasted image 20260313175646.png]]



![[Pasted image 20260313180120.png]]

```yaml
# Process nginx access log
awk -F'[][]' '{print "[" $2 "]", "--- /var/log/gitlab/nginx/access.log ---", "\"" $0 "\""}' /var/log/gitlab/nginx/access.log  | sed "s/ +0000//g" > /tmp/parsed_consolidated.log

# Process rsyslog_cron.log
awk '{ original_line = $0; gsub(/ /, "/", $1); printf "[%s/%s/2023:%s] --- /var/log/websrv-02/rsyslog_cron.log --- \"%s\"\n", $2, $1, $3, original_line }' /var/log/websrv-02/rsyslog_cron.log >> /tmp/parsed_consolidated.log

# Process rsyslog_sshd.log
awk '{ original_line = $0; gsub(/ /, "/", $1); printf "[%s/%s/2023:%s] --- /var/log/websrv-02/rsyslog_sshd.log --- \"%s\"\n", $2, $1, $3, original_line }' /var/log/websrv-02/rsyslog_sshd.log >> /tmp/parsed_consolidated.log

# Process gitlab-rails/api_json.log
awk -F'"' '{timestamp = $4; converted = strftime("[%d/%b/%Y:%H:%M:%S]", mktime(substr(timestamp, 1, 4) " " substr(timestamp, 6, 2) " " substr(timestamp, 9, 2) " " substr(timestamp, 12, 2) " " substr(timestamp, 15, 2) " " substr(timestamp, 18, 2) " 0 0")); print converted, "--- /var/log/gitlab/gitlab-rails/api_json.log ---", "\""$0"\""}' /var/log/gitlab/gitlab-rails/api_json.log >> /tmp/parsed_consolidated.log
```

![[Pasted image 20260313180134.png]]


https://tryhackme.com/room/splunk101 [Completado]

![[Pasted image 20260311215012.png]]

![[Pasted image 20260313212003.png]]

![[Pasted image 20260313212010.png]]
![[Pasted image 20260313212022.png]]
![[Pasted image 20260313212034.png]]

![[Pasted image 20260313212352.png]]

![[Pasted image 20260313212419.png]]

![[Pasted image 20260313212430.png]]

Splunk se maneja por querys, en la documentación esta toda la info.


[link directo a operadores lógicos](https://docs.splunk.com/Special:SplunkSearch/docs?q=logical%20operators&size=n_10_n&filters%5B0%5D%5Bfield%5D=source_name_s&filters%5B0%5D%5Bvalues%5D%5B0%5D=Docs&filters%5B0%5D%5Btype%5D=any)


- https://tryhackme.com/room/splunkexploringspl [No Completado]

![[Pasted image 20260314005803.png]]

- https://tryhackme.com/room/splunk201
![[Pasted image 20260313211038.png|697]]

- https://tryhackme.com/room/benign [No Completado]


![[Pasted image 20260313211131.png]]

- https://tryhackme.com/room/investigatingwithsplunk [No Completado]

![[Pasted image 20260313211220.png]]

- https://tryhackme.com/room/investigatingwithelk101 [No Completado]

![[Pasted image 20260313211245.png]]

 - https://tryhackme.com/room/itsybitsy [No Completado]

![[Pasted image 20260313211302.png]]

- https://tryhackme.com/room/posheclipse [No Completado]

![[Pasted image 20260314005734.png]]



- https://tryhackme.com/room/windowseventlogs [Completado]


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


# Test Windows Event Log


### Scenario 1 (Questions 1 & 2) : The server admins have made numerous complaints to Management regarding PowerShell being blocked in the environment. Management finally approved the usage of PowerShell within the environment. Visibility is now needed to ensure there are no gaps in coverage. You researched this topic: what logs to look at, what event IDs to monitor, etc. You enabled PowerShell logging on a test machine and had a colleague execute various commands.

- Haciendo uso del comando webtutil podemos revisar los logs en busca del evento "Power Shell Scrypt Block Logging" (4104) y filtramos en base a si el campo ScriptBlockText contiene información, obtenemos su fecha (Date)
	wevtutil qe C:\Users\Administrator\Desktop\merged.evtx /lf:true /q:"*[System[(EventID=4104)]]" /f:text | findstr "Date ScriptBlockText"


leyendo log borrado

Get-WinEvent -Path .\Desktop\merged.evtx -FilterXPath "*[System[(EventID=4104)] and EventData[Data[@Name='ScriptBlockText']]]"  -Oldest -MaxEvents 1 | Format-List




## Información Útil


**[EVTX-ATTACK-SAMPLES](https://github.com/sbousseaden/EVTX-ATTACK-SAMPLES)**


# [PowerShell ♥ the Blue Team](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)


# [Tampering with Windows Event Tracing: Background, Offense, and Defense](https://blog.palantir.com/tampering-with-windows-event-tracing-background-offense-and-defense-4be7ac62ac63)














## Firewall Logs (Windows)

![[Pasted image 20260312174402.png]]

## Cyber Kill Chain
- https://tryhackme.com/room/cyberkillchain [No Completado]

![[Pasted image 20260312174549.png]]


## Cyber Security 101 (Path)

- https://tryhackme.com/path/outline/cybersecurity101 [No Completado]

![[Pasted image 20260312174609.png]]


## Mitre ATT&CK

- https://tryhackme.com/room/mitre [No Completado]

![[Pasted image 20260312174514.png]]

