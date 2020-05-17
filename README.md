# ahuffman.resolv
An Ansible role to configure /etc/resolv.conf

## Role Variables
### Defaults
| Variable Name | Required | Description | Default Value | Type |
| --- | :---: | --- | :---: | :---: |
|resolv_nameservers| yes | A list of up to 3 nameserver IP addresses | [] | list |
| resolv_domain | no | Local domain name | "" | string |
| resolv_search | no | List of up to 6 domains to search for host-name lookup | [] | list |
| resolv_sortlist | no | List of IP-address and netmask pairs to sort addresses returned by gethostbyname. | [] | list |
| resolv_options | no | List of options to modify certain internal resolver variables. | [] | list |


## Example Playbooks
### Role Invocation
```yaml
    - name: "Role Invocation - ahuffman.resolv Example"
      hosts: "all"
      roles:
        - role: "ahuffman.resolv"
          resolv_nameservers:
            - "8.8.8.8"
            - "8.8.4.4"
          resolv_domain: "foo.org"
          resolv_search:
            - "foo.bar"
            - "foobar.com"
          resolv_options:
            - "timeout:2"
            - "rotate"
```
### Role Invocation with externaly defined variables (group_vars / host_vars)
```yaml
    - name: "Role Invocation - ahuffman.resolv Example"
      hosts: "all"
      roles:
        - role: "ahuffman.resolv"
          when:
            - resolv_nameservers is defined
            - resolv_nameservers | length > 0
```
### Included Role
```yaml
---
- name: "Included Role - ahuffman.resolv Example"
  hosts: "all"
  tasks:
    - name: "Configure resolv.conf"
      include_role:
        name: "ahuffman.resolv"
      vars:
        resolv_nameservers:
          - "8.8.8.8"
          - "8.8.4.4"
        resolv_domain: "foo.org"
        resolv_search:
          - "foo.bar"
          - "foobar.com"
        resolv_options:
          - "timeout:2"
          - "rotate"
```
## License
[MIT](LICENSE)

## Author Information
[Andrew J. Huffman](https://github.com/ahuffman)
