Ansible Role : dginhoux.pxe_os_images
=========

This ansible role download needed linux kernel image and initrd used for PXE boot


Requirements
------------

This role require a supported platform defined in `meta/main.yml`.
It will skip node with unsupported platform ; this behaviour can be bypassed by settings this variable `asserts_bypass=True`.


Role Variables
--------------

Necessary variables are defined on `defaults/main.yml`



Dependencies
------------

none


Example Playbook
----------------



License
-------

BSD


Author Information
------------------

https://github.com/dginhoux/
