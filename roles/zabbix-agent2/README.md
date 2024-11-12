zabbix-agent2
=========

Setups zabbix-agent2

Requirements
------------

None

Role Variables
--------------

use_psk: use psk for traffic encryption
psk_key_path: path for psk key. Key can be created by running "openssl rand -hex 32 > files/zabbix_agentd.psk"

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
        - role: openvpn
          use_psk: true  # optional
          psk_key_path: "files/zabbix-agent/gateways.psk"  # optional


License
-------

BSD

Author Information
------------------

Copyright (c) 2024 Andrei Ruslantsev
