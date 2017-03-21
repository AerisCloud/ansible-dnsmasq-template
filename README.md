aeriscloud.dnsmasq-template
===========================

Install dnsmasq and configure it entirely through ansible variables.

Requirements
------------

None

Dependencies
------------

None

Example Playbooks
-----------------

#### Simple DNS setup

```yaml
- hosts: all
  roles:
    - role: aeriscloud.dnsmasq-template
      dnsmasq_servers:
        - 8.8.8.8
        - "/consul.domain/{{ consul_ip }}#8600"
      dnsmasq_addresses:
        - "/mydomain.local/{{ some_machine_ip }}"
```

#### Simple DHCP setup

```yaml
- hosts: all
  roles:
    - role: aeriscloud.dnsmasq-template
      dnsmasq_no_resolv: true
      dnsmasq_no_poll: true
      dnsmasq_servers:
        - 8.8.8.8
        - 8.8.4.4
      dnsmasq_except_interface: ppp0
      dnsmasq_dhcp_range: 192.168.1.50,192.168.1.150,12h
      dnsmasq_read_ethers: true
```

Role Variables
--------------

The role comes with a template that maps variables to the actual dnsmasq
configuration 1:1, but in some cases it might be overcomplex or too many
variables to setup, in which case you can override the `dnsmasq_template`
variable to point to your own template.

| variable         | type     |
|------------------|----------|
| dnsmasq_template | _string_ |

The only special cases are `dnsmasq_dnsseq` and entries that can have
multiple values, in which case you will get a singular version that spawns
only one line of it, and a plural version that is expected to be an array.

| variable     | type     |
|--------------|----------|
| dnsmasq_port | _string_ |
| dnsmasq_domain_needed | _bool_ |
| dnsmasq_bogus_priv | _bool_ |
| dnsmasq_dnsseq | _this is actually a string that should point to your conf-file_ |
| dnsmasq_dnsseq_check_unsigned | _bool_ |
| dnsmasq_filterwin2k | _bool_ |
| dnsmasq_resolv_file | _string_ |
| dnsmasq_strict_order | _bool_ |
| dnsmasq_no_resolv | _bool_ |
| dnsmasq_no_poll | _bool_ |
| dnsmasq_servers | _array(string)_ |
| dnsmasq_locals | _array(string)_ |
| dnsmasq_addresses | _array(string)_ |
| dnsmasq_ipsets | _array(string)_ |
| dnsmasq_aliases | _array(string)_ |
| dnsmasq_user | _string_ |
| dnsmasq_group | _string_ |
| dnsmasq_interface | _string_ |
| dnsmasq_interfaces | _array(string)_ |
| dnsmasq_except_interface | _string_ |
| dnsmasq_except_interfaces | _array(string)_ |
| dnsmasq_listen_address | _string_ |
| dnsmasq_listen_addresses | _array(string)_ |
| dnsmasq_no_dhcp_interface | _string_ |
| dnsmasq_no_dhcp_interfaces | _array(string)_ |
| dnsmasq_bind_interfaces | _bool_ |
| dnsmasq_no_hosts | _bool_ |
| dnsmasq_addn_hosts | _string_ |
| dnsmasq_expand_hosts | _bool_ |
| dnsmasq_domain | _string_ |
| dnsmasq_domains | _array(string)_ |
| dnsmasq_dhcp_range | _string_ |
| dnsmasq_dhcp_ranges | _array(string)_ |
| dnsmasq_enable_ra | _bool_ |
| dnsmasq_dhcp_host | _string_ |
| dnsmasq_dhcp_hosts | _array(string)_ |
| dnsmasq_dhcp_ignore | _string_ |
| dnsmasq_dhcp_ignores | _array(string)_ |
| dnsmasq_dhcp_vendorclass | _string_ |
| dnsmasq_dhcp_vendorclasses | _array(string)_ |
| dnsmasq_dhcp_userclass | _string_  |
| dnsmasq_dhcp_userclasses | _array(string)_ |
| dnsmasq_dhcp_mac | _string_ |
| dnsmasq_dhcp_macs | _array(string)_ |
| dnsmasq_read_ethers | _bool_ |
| dnsmasq_dhcp_option | _string_ |
| dnsmasq_dhcp_options | _array(string)_ |
| dnsmasq_dhcp_option_force | _string_ |
| dnsmasq_dhcp_option_forces | _array(string)_ |
| dnsmasq_dhcp_boot | _string_ |
| dnsmasq_dhcp_boots | _array(string)_ |
| dnsmasq_dhcp_match | _string_ |
| dnsmasq_dhcp_matches | _array(string)_ |
| dnsmasq_dhcp_lease_max | _string_ |
| dnsmasq_dhcp_leasefile | _string_ |
| dnsmasq_dhcp_authoritative | _bool_ |
| dnsmasq_dhcp_script | _string_ |
| dnsmasq_pxe_prompt | _string_ |
| dnsmasq_pxe_service | _string_ |
| dnsmasq_pxe_services | _array(string)_ |
| dnsmasq_enable_tftp | _bool_ |
| dnsmasq_tftp_root | _string_ |
| dnsmasq_tftp_no_fail | _bool_ |
| dnsmasq_tftp_secure | _bool_ |
| dnsmasq_tftp_no_blocksize | _bool_ |
| dnsmasq_cache_size | _string_ |
| dnsmasq_no_negcache | _bool_ |
| dnsmasq_local_ttl | _string_ |
| dnsmasq_bogus_nxdomain | _string_ |
| dnsmasq_bogus_nxdomains | _array(string)_ |
| dnsmasq_mx_hosts | _array(string)_ |
| dnsmasq_mx_target | _string_ |
| dnsmasq_localmx | _bool_ |
| dnsmasq_selfmx | _bool_ |
| dnsmasq_srv_hosts | _array(string)_ |
| dnsmasq_ptr_records | _array(string)_ |
| dnsmasq_txt_records | _array(string)_ |
| dnsmasq_cnames | _array(string)_ |
| dnsmasq_log_queries | _bool_ |
| dnsmasq_log_dhcp | _bool_ |
| dnsmasq_conf_file | _string_ |
| dnsmasq_conf_files | _array_ |
| dnsmasq_conf_dir | _string_ |
| dnsmasq_conf_dirs | _array_ |

License
-------

MIT

Author Information
------------------

Christophe Robin <crobin@nekoo.com>
