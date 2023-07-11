# Ansible Collection - tafeen.synology

Synology setup automation, current version was tested on DSM 7.2

Examples of usage:

1. Add accounts
```
---
- name: Provision synology server
  hosts: syno
  become: true
  tasks:
    - name: Setup Accounts
      ansible.builtin.import_role:
        name: tafeen.syno_add_accounts
      vars:
        syno_accounts:
          - name: daniel
            password: "<here goes password>"
          - name: john
            password: "<here goes password>"

```

2. Add Shares
```
- name: Provision synology server
  hosts: syno
  become: true
  tasks:
    - name: Setup Shares
      ansible.builtin.import_role:
        name: tafeen.syno_add_shares
      vars:
        syno_shares:
          - name: media
            description: MEDIA Share
            path: /volume3/media
            recycle: true
            rights:
              RO:
                - daniel
              RW: 
                - john
```

3.  Install packages
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

4. Setup crontab
```
- name: Provision synology server
  hosts: syno
  become: true
  tasks:
    - name: Setup crontab
      ansible.builtin.import_role:
        name: tafeen.syno_pkg_install
      vars:
        hour: "{{ item.hour }}"
        weekday: "{{ item.weekday }}"
        job: "{{ item.job }}"
      with_items:
        - hour: 10
          weekday: 1
          job: "/bin/do_something.sh"
```