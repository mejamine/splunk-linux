# Splunk Log Cleanup Playbook

This repository includes a playbook that **cleans up old Splunk Universal Forwarder logs** and ensures the logging service continues to function correctly.

The playbook removes old log files from the Splunk Forwarder log directory, recreates the main `splunkd.log` file if necessary, and restarts the Splunk Forwarder service.

This helps prevent excessive disk usage caused by accumulated log files while ensuring Splunk continues logging normally.

---

## Tasks:

- Verify that the Splunk log directory exists  
- Fail the playbook if the log directory is missing  
- Find Splunk log files older than the defined retention period  
- Delete old log files  
- Recreate the `splunkd.log` file  
- Restart the Splunk Universal Forwarder service  

---

## Supported Operating Systems

This playbook supports Linux systems where **Splunk Universal Forwarder** is installed in the default directory.

### Supported:
- RHEL / CentOS / Rocky / AlmaLinux  
- Fedora  
- Debian ≥ 9  
- Ubuntu  

### Not Supported (Playbook may fail):
- Systems where Splunk Forwarder is installed in a custom directory  
- Systems without `/opt/splunkforwarder` installed  

---

## Using in AAP

### General Config :

1. **Inventory:** create from file or manually  
2. **Credential:** SSH username/password + sudo  

No survey is required unless you want to override the default log path or retention policy.

---

## Variables

### Playbook Variables (defined inside the playbook)

```yaml
splunk_log_path: /opt/splunkforwarder/var/log/splunk
log_retention_days: 7