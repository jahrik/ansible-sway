Sway
=======

[![CICD](https://github.com/jahrik/ansible-sway/actions/workflows/cicd.yml/badge.svg)](https://github.com/jahrik/ansible-sway/actions/workflows/cicd.yml)

Installs and configures Sway

New to sway, but have been using i3 for a few years now. Trying wayland and sway. These are my configs.

Example Playbook
----------------

yaml```
    - hosts: laptops
      roles:
         - { role: jahrik.sway, install: true, sway.terminal: alacritty }
```

License
-------

GPLv2

Author Information
------------------

jahrik@gmail.com

https://homelab.business/
