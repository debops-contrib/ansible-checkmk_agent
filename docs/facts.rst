.. _checkmk_agent__ref_ansible_facts:

Ansible facts
=============

.. include:: includes/all.rst

The role exposes part of it’s state by means of Ansible local facts for other
roles and playbooks to use.
The interface is considered public and changes to it happen in compliance with
`Semantic Versioning`_ of the role and will be mentioned in the :ref:`checkmk_agent__ref_changelog`.
Here you can find documentation and examples for them.

Specification
-------------

``ansible_local.checkmk_agent.plugins``
  List of all Check_MK Agent plugin names which are enabled (and configured if
  necessary) by the role. Refer to :envvar:`checkmk_agent__plugins` and related
  variables for details.

  Availability: Always, after ``debops-contrib.checkmk_agent/env`` has been run.

Example
-------

.. code-block:: json

   {
       "plugins": ["nginx_status"]
   }
