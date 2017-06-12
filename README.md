[![Build Status](https://travis-ci.org/lifeofguenter/ansible-role-resolvconf.svg?branch=master)](https://travis-ci.org/lifeofguenter/ansible-role-resolvconf)

# Ansible Role: resolvconf

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

    - hosts: all
      vars:
        resolv_nameservers:
          - 8.8.8.8
          - 8.8.4.4
        resolv_domain: foo.org
        resolv_search:
          - foo.bar
          - foobar.com
        resolv_options:
          - timeout:2
          - rotate
      roles:
        - lifeofguenter.resolvconf

## License

[MIT](LICENSE)
