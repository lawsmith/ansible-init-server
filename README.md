# Initial Server Setup Playbook
This is my constantly changing playground for setting up a ubuntu box using ansible.


## What does this playbook do (so far)?
| Role          | Description
|---------------|----------------------------------------------------------------------
| base          | Runs updates, installs fail2ban, and UFW
| compatibility | Installs python2 for ansible to work on ubuntu 16
| users         | Creates an unprivileged user account with a public key
| ssh           | Locks down SSH to disable direct root login and plaintext passwords
| nginx         | Installs and configures Nginx
| letsencrypt   | Installs and configured SSL certificate from Letsencrypt


## Running the playbook
This playbook currently requires using a superuser account for all tasks to complete successfully. A template inventory is provided inside of `./inventories` that may be duplicated and used.

Running the ansible playbook may be achieved with the following command:
```
ansible-playbook playbook.yml -i inventories/enter-filename-here
```

If the superuser account doesn't have a public key and is setup instead with a plain text password, ansible will need to be ran using the `--ask-pass` argument.


## Editing Environment Variables
All env vars are found within `./vars/all.yml`.

I recommend at least changing the users password because it is a hashed password. To change it, check out the ansible [FAQ's](http://docs.ansible.com/ansible/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module) under the "How do I generate crypted passwords for the user module?" section.
