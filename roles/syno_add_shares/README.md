# Add shares

Example of usage:
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
Where
`syno_shares` - list of shares to add
  `name` - name of share
  `description` - description of share
  `path` - path to share
  `recycle` - should recycle be enabled
  `rights`
    - `RO` - list of readonly accounts
    - `RW` - list of readwrite accounts
