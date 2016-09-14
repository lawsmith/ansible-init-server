# Initial Server Setup Playbook
Despite it's long name, this is a basic ansible playbook for doing some initial setup on a server by creating a lower privileged user and locking the system down.

## Running ansible playbook
To get ansible to run on your server, copy the template file located at `./inventories/template` to `./inventories/server`. Then replace the _ENTER-IP-HERE_ with your server's IP address.

Once that's done, run the playbook with the following command
```
ansible-playbook playbook.yml -i inventories/server
```

## Generating a User Password
This playbook sets up a user account with a password. Instead of displaying the password in plain text within the playbook, we're using python's hashed password function.

### Install passlib
```
pip2 install passlib
```

### Generate password
```
python -c "from passlib.hash import sha512_crypt; import getpass; print sha512_crypt.encrypt(getpass.getpass())"
```

Copy the value given and replace the password under the users host within  `./vars/all.yml`
