# ROLE dginhoux.pxe_init_syslinux



## DESCRIPTION

This ansible role download needed linux kernel image and initrd used for PXE boot.


## REQUIREMENTS

#### SUPPORTED PLATFORMS

This role is tested on the following platforms.<br />

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye, bookworm |
| Fedora | 33, 34, 35, 36, 37, 38 |
| EL | 7, 8 |

You can set this variable `check_compatibility` to let the role skip nodes with unsupporteds platforms to avoid any compatibility problems.<br />


#### ANSIBLE VERSION

Ansible >= 2.13

#### DEPENDENCIES

None.



## INSTALLATION

#### ANSIBLE GALAXY

```shell
ansible-galaxy install dginhoux.pxe_init_syslinux
```
#### GIT

```shell
git clone https://github.com/dginhoux/ansible_role.pxe_init_syslinux dginhoux.pxe_init_syslinux
```


## USAGE

#### EXAMPLE PLAYBOOK

```yaml
- hosts: all
  roles:
    - name: start role dginhoux.pxe_init_syslinux
      ansible.builtin.include_role:
        name: dginhoux.pxe_init_syslinux
```


## VARIABLES

#### DEFAULT VARIABLES

Defaults variables defined in `defaults/main.yml` : 

```yaml
---
---
pxe_os_images_action: generate
# pxe_os_images_action: cleanup

pxe_os_images_folder: /srv/tftp/os

pxe_os_images_list:
  - name: Fedora
    state: present
    versions:
      - name: 37
        state: absent
        files:
          - name: vmlinuz
            url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/37/Server/x86_64/os/images/pxeboot/vmlinuz
          - name: initrd.img
            url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/37/Server/x86_64/os/images/pxeboot/initrd.img
      - name: 38
        state: present
        files:
          - name: vmlinuz
            url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/38/Server/x86_64/os/images/pxeboot/vmlinuz
          - name: initrd.img
            url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/38/Server/x86_64/os/images/pxeboot/initrd.img
      - name: 39
        state: present
        files:
          - name: vmlinuz
            url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/39/Server/x86_64/os/images/pxeboot/vmlinuz
          - name: initrd.img
            url: https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/39/Server/x86_64/os/images/pxeboot/initrd.img

  - name: Debian
    state: present
    versions:
      - name: Buster
        state: absent
        files:
          - name: linux
            url: http://ftp.debian.org/debian/dists/buster/main/installer-amd64/current/images/netboot/debian-installer/amd64/linux
          - name: initrd.gz
            url: http://ftp.debian.org/debian/dists/buster/main/installer-amd64/current/images/netboot/debian-installer/amd64/initrd.gz
      - name: Bullseye
        state: present
        files:
          - name: linux
            url: http://ftp.debian.org/debian/dists/bullseye/main/installer-amd64/current/images/netboot/debian-installer/amd64/linux
          - name: initrd.gz
            url: http://ftp.debian.org/debian/dists/bullseye/main/installer-amd64/current/images/netboot/debian-installer/amd64/initrd.gz
      - name: Bookworm
        state: present
        files:
          - name: linux
            url: http://ftp.debian.org/debian/dists/bookworm/main/installer-amd64/current/images/netboot/debian-installer/amd64/linux
          - name: initrd.gz
            url: http://ftp.debian.org/debian/dists/bookworm/main/installer-amd64/current/images/netboot/debian-installer/amd64/initrd.gz

  - name: clonezilla
    state: present
    versions:
      - name: any
        state: present
        files:
          - name: filesystem.squashfs
            path: files/pxe/os/clonezilla.any/filesystem.squashfs
          - name: initrd.img
            path: files/pxe/os/clonezilla.any/initrd.img
          - name: vmlinuz
            path: files/pxe/os/clonezilla.any/vmlinuz

  - name: gparted
    state: present
    versions:
      - name: any
        state: present
        files:
          - name: filesystem.squashfs
            path: files/pxe/os/gparted.any/filesystem.squashfs
          - name: initrd.img
            path: files/pxe/os/gparted.any/initrd.img
          - name: vmlinuz
            path: files/pxe/os/gparted.any/vmlinuz

```

#### DEFAULT OS SPECIFIC VARIABLES

Those variables files are located in `vars/*.yml` are used to handle OS differences.<br />
One of theses is loaded dynamically during role runtime using the `include_vars` module and set OS specifics variable's.

`NOT USED BY THIS ROLE`



## AUTHOR

Dany GINHOUX - https://github.com/dginhoux



## LICENSE

MIT
