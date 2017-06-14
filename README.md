# Initial Server Setup Playbook
This is my constantly changing playground for setting up an ubuntu box using ansible.


## What does this playbook do (so far)?
| Role          | Description
|---------------|----------------------------------------------------------------------
| base          | Runs updates, installs fail2ban, and UFW
| compatibility | Installs python2 for ansible to work on ubuntu 16
| users         | Creates an unprivileged user account with a public key
| ssh           | Locks down SSH to disable direct root login and plaintext passwords
| nginx         | Installs and configures Nginx
| letsencrypt   | Installs and configured SSL certificate from Letsencrypt
| firewall      | Sets up UFW and allows specified ports through


## Running the playbook
This playbook currently requires using a superuser account for all tasks to complete successfully. A template inventory is provided inside of `./inventories` that may be duplicated and used.

Running the ansible playbook may be achieved with the following command:
```
ansible-playbook playbook.yml -i inventories/ENTER_HOSTFILE_HERE
```


## Editing Environment Variables
All variables are found within `./vars/all.yml`. I opted for using Ansibles `lookup` method for using environment variables on the management machine.
