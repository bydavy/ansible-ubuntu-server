Ssh hardening
=========

Hardens ssh by:

* Disable empty password login
* Allow public key login and disable password login
* Allow root SSH access (yes this is weak. I will change this soon)

Example Playbook
----------------

```yaml
    - hosts: all
      roles:
         - ssh_hardening
```
