Getting started
===============

Example playbook
----------------

Here's an example playbook that uses the ``debops-contrib.checkmk_agent`` role:

.. literalinclude:: playbooks/checkmk_agent.yml
   :language: yaml


Ansible tags
------------

You can use Ansible ``--tags`` or ``--skip-tags`` parameters to limit what
tasks are performed during Ansible run. This can be used after host is first
configured to speed up playbook execution, when you are sure that most of the
configuration has not been changed.

Available role tags:

``role::checkmk_agent``
  Main role tag, should be used in the playbook to execute all of the role
  tasks as well as role dependencies.

``type::dependency``
  This tag specifies which tasks are defined in role dependencies. You can use
  this to omit them using ``--skip-tags`` parameter.

``depend-of::checkmk_agent``
  Execute all ``debops-contrib.checkmk_agent`` role dependencies in its context.

``depend::apt_preferences:checkmk_agent``
  Run ``debops.apt_preferences`` dependent role in ``debops-contrib.checkmk_agent`` context.

``depend::etc_services:checkmk_agent``
  Run ``debops.etc_services`` dependent role in ``debops-contrib.checkmk_agent`` context.

``depend::ferm:checkmk_agent``
  Run ``debops.ferm`` dependent role in ``debops-contrib.checkmk_agent`` context.

``role::checkmk_agent:plugins``
  Run tasks related to Check_MK agent plugin configuration.
