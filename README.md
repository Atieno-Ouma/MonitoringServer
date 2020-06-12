# MonitoringServer
Ansbile build for monitoring server

Initial Steps:
- Update and install dependancies
```
sudo apt update && sudo apt upgrade -y && sudo apt install ansible python3 git openssh-server -y
```
- Make sure SSH is running (if its already enabled it may throw a "Failed to enable" message, that is fine)
```
sudo systemctl start sshd && sudo systemctl enable sshd
```

Setup Ansible
- Open ansible hosts file
```
sudo nano /etc/ansible/hosts
```
- Add local host information
```
[local]
localhost ansible_connection=local ansible_python_interpreter="/usr/bin/env python3"
```
- Test that it's working
```
ansible local -m ping
```

Run the Playbook:
- Git pull the playbook
```
git clone https://github.com/tbcsec/MonitoringServer.git
```
- Make sure you are in the right directory (AKA the one you just cloned)
```
cd MonitoringServer
```
- Watch the magic
```
ansible-playbook MonitoringServer.yml --ask-pass --ask-become-pass -v
```
