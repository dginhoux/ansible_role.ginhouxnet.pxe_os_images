# ROLE dginhoux.pxe_init_syslinux



## DESCRIPTION

This ansible role download needed linux kernel image and initrd used for PXE boot.


## REQUIREMENTS

#### SUPPORTED PLATFORMS

This role require a supported platform.<br />
It will skip process with unsupported platform to avoid any compatibility problem.<br />
This behaviour can be bypassed by settings the following variable `asserts_bypass=True`.

| Platform | Versions |
|----------|----------|
| Debian | buster, bullseye |
| Fedora | 33, 34, 35, 36, 37 |
| EL | 7, 8 |

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
os_folder: /srv/tftp/os
os_list:
  - { state: absent, distrib: debian, version: stretch, filename: linux, url: "http://ftp.debian.org/debian/dists/stretch/main/installer-amd64/current/images/netboot/debian-installer/amd64/linux" }
  - { state: absent, distrib: debian, version: stretch, filename: initrd.gz, url: "http://ftp.debian.org/debian/dists/stretch/main/installer-amd64/current/images/netboot/debian-installer/amd64/initrd.gz" }   
  - { state: present, distrib: debian, version: buster, filename: linux, url: "http://ftp.debian.org/debian/dists/buster/main/installer-amd64/current/images/netboot/debian-installer/amd64/linux" }
  - { state: present, distrib: debian, version: buster, filename: initrd.gz, url: "http://ftp.debian.org/debian/dists/buster/main/installer-amd64/current/images/netboot/debian-installer/amd64/initrd.gz" }
  - { state: present, distrib: debian, version: bullseye, filename: linux, url: "http://ftp.debian.org/debian/dists/bullseye/main/installer-amd64/current/images/netboot/debian-installer/amd64/linux" }
  - { state: present, distrib: debian, version: bullseye, filename: initrd.gz, url: "http://ftp.debian.org/debian/dists/bullseye/main/installer-amd64/current/images/netboot/debian-installer/amd64/initrd.gz" }
  # - { state: present, distrib: centos, version: 7, filename: vmlinuz, url: "http://mirror.centos.org/centos/7/os/x86_64/isolinux/vmlinuz" }
  # - { state: present, distrib: centos, version: 7, filename: initrd.img, url: "http://mirror.centos.org/centos/7/os/x86_64/isolinux/initrd.img" }
  # - { state: present, distrib: centos, version: 8, filename: vmlinuz, url: "http://mirror.centos.org/centos/8/BaseOS/x86_64/os/isolinux/vmlinuz" }
  # - { state: present, distrib: centos, version: 8, filename: initrd.img, url: "http://mirror.centos.org/centos/8/BaseOS/x86_64/os/isolinux/initrd.img" }
  - { state: absent, distrib: fedora, version: 32, filename: vmlinuz, url: "https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/32/Server/x86_64/os/images/pxeboot/vmlinuz" }
  - { state: absent, distrib: fedora, version: 32, filename: initrd.img, url: "https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/32/Server/x86_64/os/images/pxeboot/initrd.img" }
  - { state: present, distrib: fedora, version: 33, filename: vmlinuz, url: "https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/33/Server/x86_64/os/images/pxeboot/vmlinuz" }
  - { state: present, distrib: fedora, version: 33, filename: initrd.img, url: "https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/33/Server/x86_64/os/images/pxeboot/initrd.img" }
  - { state: present, distrib: fedora, version: 34, filename: vmlinuz, url: "https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/34/Server/x86_64/os/images/pxeboot/vmlinuz" }
  - { state: present, distrib: fedora, version: 34, filename: initrd.img, url: "https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/34/Server/x86_64/os/images/pxeboot/initrd.img" }
  - { state: present, distrib: fedora, version: 35, filename: vmlinuz, url: "https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/35/Server/x86_64/os/images/pxeboot/vmlinuz" }
  - { state: present, distrib: fedora, version: 35, filename: initrd.img, url: "https://ftp.lip6.fr/ftp/pub/linux/distributions/fedora/releases/35/Server/x86_64/os/images/pxeboot/initrd.img" }
```

#### DEFAULT OS SPECIFIC VARIABLES

Those variables files are located in `vars/*.yml` are used to handle OS differences.<br />
One of theses is loaded dynamically during role runtime using the `include_vars` module and set OS specifics variable's.

`NOT USED BY THIS ROLE`



## AUTHOR

Dany GINHOUX - https://github.com/dginhoux



## LICENSE

MIT
