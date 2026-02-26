# Sysstat Installation and Configuration

This repository includes a playbook that installs and configures **sysstat** on Linux systems (Debian and RedHat families).  

It ensures the package is installed, enabled, configured, and properly collecting performance statistics.

---

## Tasks:

- Check if sysstat is already installed  
- Install sysstat package if not present  
- Enable and start sysstat service  
- Configure sysstat (Debian / RedHat families)  
- Restart service after configuration  
- Configure cron job for data collection (Debian)  
- Enable systemd timer (if available)  
- Validate installation using `sar -V`  

---

## Supported Operating Systems

- Debian / Ubuntu  
- RedHat / Fedora / CentOS  

---

## Using in AAP

### General Config :
1. **Inventory:** create from file or manually  
2. **Credential:** SSH username/password + sudo  

No survey is required because this playbook does not depend on user-defined variables.

---

## Variables

### Playbook Variables (already defined inside the playbook)

- `sysstat_config_file_debian` → `/etc/default/sysstat`  
- `sysstat_config_file_redhat` → `/etc/sysconfig/sysstat`  
- `sysstat_enabled_value` → `"true"`  

---

### Hosts variables : (in hosts.ini or create manually in AAP) (inventory related)

- `ansible_host` – ip address of the host  
- `ansible_user` – username of the host user  
- `ansible_os_family` – OS family (Debian / RedHat)  



