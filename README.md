# Security Initiative for hardening Audit Configuration and config what all is logged in audit logs

* Prerequisits:
-rw-r--r-- 1 root bin 3.9K Sep 12 22:38 /automation/light_audit.rules
if you copy /automation/manjesh/auditConf_chg.sh to different DC make sure to copy the above file too:

* How to run the /automation/manjesh/auditConf_chg.sh

As deployer user from rundeck server, run as below.

* Backout plan: 
 Copy the previous files back and restart services (auditd and rsyslog)
  - audit.rules.PreAuditFix
  - auditd.conf.PreAuditFix
  - rsyslog.conf.PreAuditFix

* Single Host:
 pssh -H 10.4.198.233 -i "-O StrictHostKeyChecking=no" -t 60 "sudo /automation/manjesh/auditConf_chg.sh"

* Multiple Host:
 pssh -h HostList -i "-O StrictHostKeyChecking=no" -t 60 "sudo /automation/manjesh/auditConf_chg.sh"


* Output:
 pssh -H 10.4.198.233 -i "-O StrictHostKeyChecking=no" -t 60 "sudo /automation/manjesh/auditConf_chg.sh"
[1] 21:46:41 [SUCCESS] 10.4.198.233
local6.*                                -/var/log/audit/audit.log
write_logs = no
log_format = ENRICHED
Success:New light_audit.rules applied, auditd.conf and rsyslog.conf updated !
        Above are the changes to rsyslog.conf and auditd.conf !

