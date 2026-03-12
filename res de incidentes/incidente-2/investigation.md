# DFIR Investigation Report

## 1. System Information

**Primary User**
- root

**Other Users Detected**
- ubuntu
- cybert
- it-admin

**System Details**

| Field | Value |
|------|------|
| OS | Ubuntu 20.04.06 LTS |
| Host IP | 10.67.173.66 |

---

# 2. User and Privilege Analysis

## Sudoers Detected

The following users have sudo privileges:

- root
- cybert
- it-admin

This is notable because the user **it-admin was created during the investigation timeline and granted sudo privileges shortly after creation.**

---

# 3. Network Activity Analysis

Logs indicate **SSH connections to the system using the root account**.

## Connection 1

| Field | Value |
|------|------|
| Local IP | 10.67.173.66 |
| Local Port | 22 |
| External IP | 10.67.127.31 |
| External Port | 34086 |
| State | ESTABLISHED |

### Associated Process

| Field | Value |
|------|------|
| PID | 920 |
| Process | ssh: root@pts/ |
| Start Time | 12:15 |
| Parent PID | 793 |

### Parent Process
/usr/sbin/ssh -D [listener] 0 of 10-100 startups


---

## Connection 2

| Field | Value |
|------|------|
| Local IP | 10.67.173.66 |
| Local Port | 22 |
| External IP | 10.67.127.37 |
| External Port | 34094 |
| State | ESTABLISHED |

### Associated Process

| Field | Value |
|------|------|
| PID | 1059 |
| Process | ssh: root@pts/ |

The parent process for this connection could not be identified, likely because the process had already terminated.

---

# 4. Log Analysis

Primary log analyzed: /var/log/auth.log.1


The current `auth.log` did not contain relevant entries.

### Suspicious Activity

Evidence of software installation originating from the user directory: /home/cybert


Command executed: /usr/bin/apt install dokuwiki


After execution:

- A new user **it-admin** was created
- The user was added to the **sudoers group**

Timestamp: December 28 - 06:27:34


This behavior suggests **possible privilege escalation or persistence preparation**.

---

# 5. Command History Analysis

Analysis of **bash history and editor usage** revealed attacker activity.

Commands indicate:

- Download of a malicious script
- Editing files using `vi`
- Creation of cron persistence

---

# 6. Persistence Investigation

## Malicious Script Download

Source IP: 10.10.158.38


Downloaded file: bomb.sh


This script indicates the presence of a **fork bomb attack**.

### Observed Sequence of Events

1. Script downloaded from remote host
2. Script opened with `vi`
3. Script renamed to: os-update.sh


4. Script added to a **cron job**

---

# 7. Cron Persistence Mechanism

The attacker modified the system cron configuration.

The scheduled job executes the script: os-update.sh


### Execution Behavior

The script is configured to:

- Create a file named: goodbye.txt


- Execution scheduled **90 days after the cron job creation**

This suggests a **delayed execution persistence mechanism** designed to trigger after a long period.

---

# 8. Indicators of Compromise (IOCs)

| Type | Value |
|-----|------|
| Attacker IP | 10.67.127.31 |
| Attacker IP | 10.67.127.37 |
| Download Source | 10.10.158.38 |
| Malicious Script | bomb.sh |
| Persistence Script | os-update.sh |
| Created File | goodbye.txt |
| Suspicious User | it-admin |

---

# 9. Timeline of Events

| Time | Event |
|-----|------|
| Dec 28 - 06:27:34 | User `it-admin` created |
| Dec 28 | User added to sudoers |
| Dec 28 | `dokuwiki` installed |
| Dec 28 | `bomb.sh` downloaded |
| Dec 28 | Script edited using `vi` |
| Dec 28 | Script renamed to `os-update.sh` |
| Dec 28 | Cron job created |

---

# 10. Attack Summary

The investigation identified a system compromise involving the following actions:

1. SSH access to the system using the **root account**
2. Creation of a new privileged user **it-admin**
3. Installation of software (`dokuwiki`)
4. Download of a malicious script (`bomb.sh`)
5. Script modification and renaming (`os-update.sh`)
6. Persistence established via **cron job**
7. Delayed payload execution designed to trigger after **90 days**

The attacker demonstrated **basic persistence techniques and privilege manipulation** within the compromised system.

---

# 11. Recommended Actions

- Remove malicious cron entries
- Delete the script `os-update.sh`
- Remove the unauthorized user `it-admin`
- Review SSH access logs
- Rotate credentials for all privileged accounts
- Disable direct root SSH login
- Implement centralized logging and monitoring