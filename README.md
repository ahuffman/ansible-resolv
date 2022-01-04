# lifeofguenter.resolvconf

[![Build Status](https://travis-ci.com/lifeofguenter/ansible-role-resolvconf.svg?branch=main)](https://travis-ci.com/lifeofguenter/ansible-role-resolvconf)

An Ansible role to configure /etc/resolv.conf

## Role Variables

### Defaults
* resolv_nameservers: ''
A list of up to 3 nameservers

* resolv_domain: ''
Local domain name

* resolv_search: ''
List of up to 6 domains to search for host-name lookup

* resolv_sortlist: ''
List of IP-address and netmask pairs to sort addresses returned by gethostbyname.

* resolv_options: ''
List of options to modify certain internal resolver variables.


## Example Playbook

```yaml
- hosts: all
  vars:
    resolv_nameservers:
      - 1.1.1.1
      - 8.8.8.8
    resolv_domain: foo.org
    resolv_search:
      - foo.bar
      - foobar.com
    resolv_options:
      - timeout:2
      - rotate
  roles:
    - lifeofguenter.resolvconf
```

## License

[MIT](LICENSE)
