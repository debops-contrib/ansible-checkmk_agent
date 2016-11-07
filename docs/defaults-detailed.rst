Default variable details
================================

Some of the ``debops-contrib.checkmk_agent`` default variables have more
extensive configuration values than simple strings or lists, here you can
find documentation and examples for them.

.. contents::
   :local:
   :depth: 1

.. _checkmk_agent__ref_host_attributes:

checkmk_agent__host_attributes
------------------------------

This is a configuration dictionary defining the host attributes which are
associated with this host in the Check_MK server Web interface (aka WATO).
The following configuration keys are supported:

``alias``
  Optional. A comment or description of this host.

``contactgroups``
  Optional. Only members of the contact groups listed here have WATO
  permission to this host. The value for this configuration key is another
  dictionary where the following configuration keys must be defined:

  ``groups``
    Required. List of contact groups defined in WATO.

  ``use_for_services``
    Optional. With this option contact groups that are added to hosts are
    always being added to services, as well. This only makes a difference
    if you have assigned other contact groups to services via rules in
    *Host & Service Parameters*. Allowed values are ``True`` and ``False``.
    Defaults to ``False``.

``ipaddress``
  Optional. In case the name of the host is not resolvable via
  :file:`/etc/hosts` or DNS by your monitoring server, you can specify an
  explicit IP address or a resolvable DNS name of the host here.

``parents``
  Optional. List of host names which act as parents. Parents are used to
  configure the reachability of hosts by the monitoring server. A host is
  considered to be unreachable if all of its parents are unreachable or down.

``site``
  Optional. Name of the monitoring site that should monitor this host.

``tag_<wato_tag>``
  Optional. Any tag defined in the WATO Web interface or when using the server
  role via ``checkmk_server__multisite_cfg_wato_host_tags`` can be assigned
  here. Example: To set the WATO tag ``criticality`` to ``test`` this would be
  defined as ``tag_criticality: test``.
