# Add shares

Example of usage:
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
Where
`syno_accounts` - list of accounts to add
- `name` - account name
- `password` - password used with account