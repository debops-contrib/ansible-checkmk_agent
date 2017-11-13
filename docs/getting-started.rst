Getting started
===============

.. include:: includes/all.rst

Example inventory
-----------------

You can install Check_MK agent on a host by adding it to the
``[debops_service_checkmk_agent`` host group in your Ansible inventory::

    [debops_service_checkmk_agent]
    hostname

Example playbook
----------------

Here's an example playbook that uses the ``debops-contrib.checkmk_agent`` role:

.. literalinclude:: playbooks/checkmk_agent.yml
   :language: yaml

The playbook is shipped with this role under
:file:`docs/playbooks/checkmk_agent.yml` from which you can symlink it to your
playbook directory.

As you can see in this example playbook, the role makes use of a number of other roles to setup it’s environment.
Some of these dependency roles are only needed when services are detected.
This is true for the debops.mariadb_ role which is used to manage a database
user used to monitor the DBMS and databases by an automatically setup
and configured agent plugin. To ensure that
:envvar:`checkmk_agent__combined_plugins` is valid in the context of other
roles (in the same playbook) this variable is based on Ansible facts which are
setup by the ``debops-contrib.checkmk_agent/env`` role prior to other
dependency roles being called.
For more details, refer to :envvar:`checkmk_agent__plugin_autodetect`.

Ansible tags
------------

You can use Ansible ``--tags`` or ``--skip-tags`` parameters to limit what
tasks are performed during Ansible run. This can be used after a host was first
configured to speed up playbook execution, when you are sure that most of the
configuration is already in the desired state.

Available role tags:

``role::checkmk_agent:env``
  Environment role tag, should be used in the playbook to execute a special
  environment role contained in the main role. The environment role prepares
  the environment for other dependency roles to work correctly.

``role::checkmk_agent``
  Main role tag, should be used in the playbook to execute all of the role
  tasks as well as role dependencies.

``role::checkmk_agent:pkgs``
  Tasks related to system package management like installing or
  removing packages.

``role::checkmk_agent:plugins``
  Run tasks related to Check_MK agent plugin configuration.

``role::checkmk_agent:plugins:get``
  Run tasks related to Check_MK agent plugin retrieval.
