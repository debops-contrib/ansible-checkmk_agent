Changelog
=========

.. include:: includes/all.rst

**debops-contrib.checkmk_agent**

This project adheres to `Semantic Versioning <http://semver.org/spec/v2.0.0.html>`__
and `human-readable changelog <http://keepachangelog.com/en/0.3.0/>`__.

The current role maintainer_ is ganto_.


`debops-contrib.checkmk_agent master`_ - unreleased
---------------------------------------------------

.. _debops-contrib.checkmk_agent master: https://github.com/debops-contrib/ansible-checkmk_agent/compare/v0.1.1...master

Added
~~~~~

- New inventory variable :envvar:`checkmk_agent__server_inventory_group` which
  can be used to define custom Ansible host group name for Check_MK server
  lookup. [ganto_]

Changed
~~~~~~~

- Raise HTTP timeout for discovery and activation WebAPI calls to 120s to avoid
  timeout issues on large hosts with many service checks. [ganto_]

- If possible run WebAPI invocation for automated agent registration and host
  attribute updates on the Check_MK server to avoid possible firewall issues.
  [ganto_]

Fixed
~~~~~

- Correctly use Ansible `changed` task filter. [ganto_]


`debops-contrib.checkmk_agent v0.1.1` - 2017-01-23
--------------------------------------------------

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
