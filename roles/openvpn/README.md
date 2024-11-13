OpenVPN
=========

Setup openvpn server

Requirements
------------

Works only on debian-like systems. Network interface should have a name eth0. It should be renamed 
or files/ufw-rules.patch should be changed

1. Build CA:

- Create directory ~/ca/easyrsa
- Create symbolic links to easyrsa, openssl-easyrsa.cnf, x509-types inside ~/ca/easyrsa
- Copy files/build-server.sh to ~/ca
- Change directory to ~/ca and run build-server.sh

2. Apply role:

It will install all needed software (openvpn, ufw, patch), apply patches to ufw configs, 
allow connections, copy openvpn keys, and start the server.

3. Generate keys for the clients:

- Copy files/build-client.sh to ~/ca
- Copy files/client.conf to ~/ca
- Edit ~/ca/client.conf and change my-server-1 to fqdn/ip address in the line `remote my-server-1 1194`
- Change directory to ~/ca
- Run build-client.sh client.conf client-name

4. Revoke keys (untested)

- Copy files/revoke-client.sh to ~/ca
- Change directory to ~/ca
- Run revoke-client.sh client-name
- Manually copy ~/ca/server/crl.pem to /etc/openvpn/server on the server
- Uncomment line in client.conf to use crl

Role Variables
--------------

None

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
        - role: openvpn

License
-------

BSD

Author Information
------------------

Copyright (c) 2023 Andrei Ruslantsev
