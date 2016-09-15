# Initial Server Setup Playbook
This is my constantly changing playground for setting up a basic ubuntu box using ansible.

## What does this playbook do?
- Sets up an unprivileged user account
- Disables direct SSH login with root
- Forces public key authentication for SSH
- Enables Ubuntu's UFW

## Running the playbook
Currently this playbook requires using a root or superuser account for all tasks to complete successfully. I've made a template inventory file inside of `./inventories` that made be duplicated and used. There are two ways I recommend running ansible, depending on your initial server setup.

The first option assumes that the root account already has a public key
```
ansible-playbook playbook.yml -i inventories/server
```

The second option assumes that the root account is using a plain text password
```
ansible-playbook playbook.yml -i inventories/server --ask-pass
```

## Editing Environment Variables
All env vars are found within `./vars/all.yml`.

I recommend at least changing the users password because it is a hashed password. To change it, check out the ansible [FAQ's](http://docs.ansible.com/ansible/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module) under the "How do I generate crypted passwords for the user module?" section.
