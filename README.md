This [Ansible](http://ansible.com/) role allows you to install and manage
the [Check_MK](https://mathias-kettner.com/check_mk.html) agent. It is the
client component of the Nagios-like Check_MK monitoring suite.


### Installation

This role requires at least Ansible `v1.7.0`. To install it, clone it
to your [DebOps](http://debops.org) project roles directory:

    git clone https://github.com/debops-contrib/ansible-checkmk_agent.git


### Role dependencies

- `debops.apt_preferences`
- `debops.etc_services`
- `debops.ferm`

### Are you using this as a standalone role without DebOps?

You may need to include missing roles from the [DebOps common
playbook](https://github.com/debops/debops-playbooks/blob/master/playbooks/common.yml)
into your playbook.

[Try DebOps now](https://github.com/debops/debops) for a complete solution to run your Debian-based infrastructure.



### Authors and license

`checkmk_agent` role was written by:
- Reto Gantenbein | [e-mail](mailto:reto.gantenbein@linuxmonk.ch) | [GitHub](https://github.com/ganto)

License: [GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)
