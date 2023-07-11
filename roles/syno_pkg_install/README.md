# Install pacakges available in Package Center

Example of usage:
```
- name: Provision synology server
  hosts: syno
  become: true
  tasks:
    - name: Setup packages
      ansible.builtin.import_role:
        name: tafeen.syno_pkg_install
      vars:
        syno_upgrade_packages: true
        syno_packages:
            - Docker
            - FileStation
```
Where
`syno_upgrade_packages` - should synology update already installed packages (not required)
`syno_packages` - list of packages to be installed (not required)
