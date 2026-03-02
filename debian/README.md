# Splunk Universal Forwarder Installation and Configuration

This repository includes a playbook that installs and configures the **Splunk Universal Forwarder (UF)** on Linux systems (Debian and RedHat families).  

It ensures the forwarder is installed, started, configured with an admin password, and the Splunk Cloud UF app is deployed.

---

## Tasks:


- Create `/opt/splunkforwarder` directory  
- Download the Splunk UF package 
- Set correct permissions on the downloaded package  
- Install Splunk UF    
- Create user seed
- Start Splunk Forwarder and accept license 
- Create log file 
- Restart splunk forwarder
- Copy Splunk Cloud UF credentials package from the playbook to the host  
- Install the Splunk Cloud UF app using the admin credentials  
- Restart Splunk Forwarder to apply changes  

---

## Supported Operating Systems

- Debian / Ubuntu  

---

## Using in AAP / Ansible

### General Config:

1. **Inventory:** create from file or manually  
2. **Credential:** SSH username/password with sudo  

### Survey:

- `splunk_pass` → This is the Splunk Universal Forwarder admin password. It is intentionally left empty in the playbook and should be set via **survey** at runtime.  

No other survey input is required as all other variables are predefined.

---

## Variables

### Playbook Variables (already defined inside the playbook)

- `splunk_uf_deb_url` → URL for the Debian package of Splunk UF  
- `splunk_pass` → Splunk Forwarder admin password (to be provided via survey)  


---

### Hosts variables (inventory related)

- `ansible_host` – IP address of the host  
- `ansible_user` – SSH username for the host  

---

## Notes:

- The playbook is **idempotent**: it will not reinstall or overwrite if the forwarder or app is already present.  
- The Splunk admin password is stored via **survey** and not hardcoded.  
- Ownership of `/opt/splunkforwarder` is set to the `splunkfwd` user for proper forwarder operation.  
- Ensure the Splunk Cloud UF credentials package (`splunkclouduf.spl`) is present in the `files/` directory of the playbook before running.