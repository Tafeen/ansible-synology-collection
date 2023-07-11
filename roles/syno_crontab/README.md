# Setup crontab

Example of usage:
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
        - job: "/bin/do_something.sh"
          minute: "0"
          hour: "12"
          month: "*"
          weekday: "1"
          user: "root"
```

Where
`minute` - minute that script should run (0-59 or *, default: "0")
`hour` - hour that script should run (1-24 or *, default: "12")
`weekday` - weekday that script should run (1-7 or *, default: "1") or `monthday` - monthday that script should run (day of month or *)
`month` - month that script should run (1-12 or *, default: "*")
`user` - script will run as user (default: "root")
`job` - command or script to be run (required)