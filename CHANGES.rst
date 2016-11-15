Changelog
=========

.. include:: includes/all.rst

**debops-contrib.checkmk_agent**

This project adheres to `Semantic Versioning <http://semver.org/spec/v2.0.0.html>`__
and `human-readable changelog <http://keepachangelog.com/en/0.3.0/>`__.

The current role maintainer_ is ganto_.


`debops-contrib.checkmk_agent master`_ - unreleased
---------------------------------------------------

.. _debops-contrib.checkmk_agent master: https://github.com/debops-contrib/ansible-checkmk_agent/compare/v0.1.0...master

Security
~~~~~~~~

- Change git clone URL used to install additional plugins from ``http://`` to
  https://git.mathias-kettner.de/check_mk.git to mitigate potential MITM
  attacks against the unauthenticated ``http://`` connection.
  That, together with using the latest git master branch by default could
  result in malicious code being executed on systems where the agent is
  installed.
  It needs to be checked if already configured hosts are updated to
  ``https://`` by subsequent role runs. [ypid_]


debops-contrib.checkmk_agent v0.1.0 - 2016-11-07
------------------------------------------------

Added
~~~~~

- Initial release [ganto_]
