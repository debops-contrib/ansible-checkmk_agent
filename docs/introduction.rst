Introduction
============

This `Ansible`_ role allows you to install and manage the `Check_MK`_
agent. It is the client component of the nagios-based Check_MK monitoring
suite.

Because the ``check-mk-agent`` package is missing in the Debian Jessie
release, this role depends on the `debops.backporter`_ role to rebuild
the Stretch sources for Jessie.

.. _Ansible: http://ansible.com/
.. _Check_MK: https://mathias-kettner.com/check_mk.html
.. _debops.backporter: http://github.com/debops/ansible-backporter

..
 Local Variables:
 mode: rst
 ispell-local-dictionary: "american"
 End:
