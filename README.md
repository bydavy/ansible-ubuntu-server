# Configure your Ubuntu Server

This playbook is a turnkey configuration for you ubuntu server with sain security/safety.

* Boot on small ssh server and ask for password to decrypt rootfs and starts Ubuntu Server
* Hardened ssh security
* Installs faild2ban & mosh

## Steps
1. Install Ubuntu Server
  * Select "Guided - user entire disk and set up encrypted LVM"
![Ubunter Server Installation](docs/ubuntu_guided_use_encrypted_lvm.png)
2. Update variables in `group_vars/vars.yml`
3. Update `ansible_host`, `ansible_user`, `ansible_port` in `hosts`
5. `$ ansible-galaxy install -r requirements.yml.`
6. `$ ansible-playbook playbook.yml  --ask-become-pass`

## Boot process

Dropbear will boot first and have an ssh server running waiting for you to unlock the rootfs for the OS.
Connect with `$ ssh -p <ssh_port> -o "UserKnownHostsFile=/dev/null" root@192.168.1.100`, then `$ cryptroot-unlock` and enter the password.
Your data is now accessible and the OS will finally boot.

You can now ssh into your Ubuntu server
`$ ssh -p <ssh_port> ubuntu@192.168.1.10`

## Sources
* LUKS encryption
  * [askubuntu.com](https://askubuntu.com/questions/1269981/unattended-headless-ubuntu-server-with-disk-encryption-how-to-set-it-up)
  * [suenotek.com](https://blog.suenotek.com/post/ubuntu-20-04-full-disk-encryption-luks-on-the-cloud/)