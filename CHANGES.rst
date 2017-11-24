.. _checkmk_agent__ref_changelog:

Changelog
=========

.. include:: includes/all.rst

**debops-contrib.checkmk_agent**

This project adheres to `Semantic Versioning <http://semver.org/spec/v2.0.0.html>`__
and `human-readable changelog <http://keepachangelog.com/en/0.3.0/>`__.

The current role maintainer_ is ganto_.


`debops-contrib.checkmk_agent master`_ - unreleased
---------------------------------------------------

.. _debops-contrib.checkmk_agent master: https://github.com/debops-contrib/ansible-checkmk_agent/compare/v0.2.0...master



`debops-contrib.checkmk_agent v0.2.0`_ - 2017-11-24
---------------------------------------------------

.. _debops-contrib.checkmk_agent v0.2.0: https://github.com/debops-contrib/ansible-checkmk_agent/compare/v0.1.1...v0.2.0

Added
~~~~~

- New inventory variable :envvar:`checkmk_agent__server_inventory_group` which
  can be used to define custom Ansible host group name for Check_MK server
  lookup. [ganto_]

- Support :envvar:`checkmk_agent__deploy_state`. [ypid_]

- Automatically enable the ``smart`` Check_MK agent plugin on physical hosts to
  query Self-Monitoring, Analysis and Reporting data from disks. [ypid_]

- Add :ref:`checkmk_agent__ref_ansible_facts` documentation. [ypid_]

- Add :envvar:`checkmk_agent__git_dest_host` which can be used to clone the
  Check_MK only once to the Ansible controller. [ypid_]

Changed
~~~~~~~

- Raise HTTP timeout for discovery and activation WebAPI calls to 120s to avoid
  timeout issues on large hosts with many service checks. [ganto_]

- If possible run WebAPI invocation for automated agent registration and host
  attribute updates on the Check_MK server to avoid possible firewall issues.
  [ganto_]

- Rename ``checkmk_agent__hostname`` to :envvar:`checkmk_agent__fqdn`. You might need
  to update your inventory. [ypid_]

- Rename ``checkmk_agent__group_plugin_map`` to :envvar:`checkmk_agent__facts_plugin_map`. You might need
  to update your inventory. [ypid_]

- Increase Ansible min version to ``2.1.5``. Everything below is deprecated
  anyway and has vulnerabilities so you don’t want to use that anymore. [ypid_]

Removed
~~~~~~~

- Remove the ``debops_checkmk_agent`` Ansible inventory group. Make sure your
  hosts are in ``debops_service_checkmk_agent``. [ypid_]

Fixed
~~~~~

- Correctly use Ansible `changed` and `skipped` task filters. [ganto_]

- Let xinetd bind on ``AF_INET6`` to ensure IPv6 reachability of the agent. [ypid_]

- Fix TCP Wrappers support for xinetd. [ypid_]

- Ensure the :file:`/etc/check_mk` directory is present before running
  dependency roles. Fixes MariaDB credentials configuration. [ypid_]

Security
~~~~~~~~

- Enforce known good git commit hashes. As upstream does not cryptographically sign their work,
  the known good hashes have to be pinned manually in
  :envvar:`checkmk_agent__git_version_map` of the role. [ypid_]


`debops-contrib.checkmk_agent v0.1.1`_ - 2017-01-23
---------------------------------------------------

.. _debops-contrib.checkmk_agent v0.1.1: https://github.com/debops-contrib/ansible-checkmk_agent/compare/v0.1.0...v0.1.1

Added
~~~~~

- ``role::checkmk_agent:plugins:get`` Ansible tag for cloning/pulling related
  tasks. [ypid_]

Changed
~~~~~~~

- Run the debops.ferm_ role also when :program:`xinetd` is not listed in
  :envvar:`checkmk_agent__type` to allow to migrate between different types. [ypid_]

Fixed
~~~~~

- Fix :program:`xinetd` support which is filtered by ``tcpwrappers`` and which is
  configured by debops.tcpwrappers_ to deny all connections by default
  (whitelisting). [ypid_]

- Fix lookup of non-default monitoring site specified as Ansible local fact by
  the debops-contrib.checkmk_server_ role. [ganto_]

Security
~~~~~~~~

- Change git clone URL used to install additional plugins from ``http://`` to
  https://git.mathias-kettner.de/check_mk.git to mitigate potential MITM
  attacks against the unauthenticated ``http://`` connection.
  That, together with using the latest git master branch by default could
  result in malicious code being executed on systems where the agent is
  installed.
  :command:`git pull` will use the new URL from now on.
  Note that "GnuTLS recv error[s]" have been observed which might have to be
  fixed elsewhere. "GnuTLS recv error (-9): A TLS packet with unexpected length
  was received" [ypid_]


debops-contrib.checkmk_agent v0.1.0 - 2016-11-07
------------------------------------------------

Added
~~~~~

- Initial release [ganto_]
