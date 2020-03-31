************
Requirements
************

Ericom Shield can be deployed in various deployments and topologies. The most common use cases are detailed `here <../deploymentguide/shieldarchitecture.html#use-cases>`_.
The requirements detailed hereunder are per a single machine deployment and per multi machine deployment. 

Requirements for Ericom Shield
==============================

Hardware Requirements
---------------------

.. csv-table::
    :header: "", "Minimum", "Recommended", "Recommended (ELK)"
    :widths: 10, 10, 10, 10

    Core processors, 8, 12, 12
    Memory (GB), 16, 16, 16
    Disk (GB), 100, 100, 256

.. note:: For improved performance, **SSD** disk is recommended

The **maximum** number of cores per node is 24. When there are more than 16 cores per node, increasing the number of pods per node is required. For more details, see `here <FAQ/increasepods.html>`_.

.. note:: Ericom Shield supports both horizontal and vertical scaling. Horizontal scaling means adding more machines to the system. Vertical scaling means adding more hardware to the system. A higher spec machine will host more virtual containers and therefore more browser sessions. For further information on scaling and how to determine the exact required hardware per usage, please contact Ericom Shield Professional Services.

Software Requirements
---------------------

*   Linux Ubuntu Server 16.04 or 18.04 (64-bit, not workstation) or CentOS 7.6-1810 (x86) with Kernel 4.4
*   Has a fixed IP Address
*   Has a unique hostname
*   Has the same timezone (as other machines in the system)
*   Has SSH server installed
*   Has an internet connection (DNS and Proxy settings are configured properly)
*   Locale is EN-US

.. note:: RHEL is also supported. If this is the selected OS, please contact Ericom Shield Professional Services.

In case partitioning is planned (not mandatory for Shield, only optional), here are the recommended sizes for the different partitions:

*   /boot - 0.5 GB
*   /var/log - 10GB
*   /tmp - 10GB
*   / (root) - (including /var/lib) - rest of the disk

.. note:: Other file systems on the server are not used/relevant for Shield, and do not require specific disk allocation. They can all be included under /root.

When using Ubuntu, it is recommended to turn ON the **Ubuntu Security Automatic Updates** on the host server. Further details can be found `here <https://help.ubuntu.com/lts/serverguide/automatic-updates.html>`_.

When using CentOS, if a Kernel update is required, please follow the instructions `here <FAQ/centos.html>`_.

Connectivity
------------

**Ports** 

Ericom Shield requires these ports to be open on the network:

.. csv-table::
    :header: "Port", "Protocol", "From", "To", "Comment"
    :widths: 10, 10, 10, 10, 10
    
    3128, TCP, End users, Shield Proxy servers, "Inbound between End-Users and Shield"
    8443, TCP, "", Rancher, "Inbound and between all Shield servers. Used to connect to the Rancher Administration Console and between Shield servers to Rancher server"
    30181, TCP, Admin Users, Shield-Management, "Inbound. Used to connect to the Shield Administration Console"
    SSH 22, TCP, Shield, Shield, "Inbound and between all Shield servers. "
    2376, TCP, Shield, Shield, "Between all Shield servers"
    2379, TCP, Shield, Shield, "Between all Shield servers"
    2380, TCP, Shield, Shield, "Between all Shield servers"
    4789, UDP, Shield, Shield, "Between all Shield servers"
    6443, TCP, Shield, Shield, "Between all Shield servers"
    8472, UDP, Shield, Shield, "Between all Shield servers"
    9099, TCP, Shield, Shield, "Between all Shield servers"
    10250, TCP, Shield, Shield, "Between all Shield servers"
    10254, TCP, Shield, Shield, "Between all Shield servers"
    389, TCP, Shield Proxy, LDAP Server, "Between Shield and LDAP server"
    636, TCP, Shield Proxy, LDAPS Server, "Between Shield and LDAP server"
    88, TCP, Shield Proxy, AD-Kerberos, "Required when using Kerberos authentication"
    88, UDP, Shield Proxy, AD-Kerberos, "Required when using Kerberos authentication"
    80, TCP, Shield, Internet, "Outbound internet connection"
    443, TCP, Shield, Internet, "Outbound internet connection"
    53, TCP, Shield, DNS, ""
    53, UDP, Shield, DNS, ""
    25, TCP, Shield-Management/Browser Farm, SMTP server, "Required when using SMTP for alerts and statistics"
    
    	

**DNS & Subnet**

Ericom Shield uses the Linux Host DNS configuration to identify which DNS server to use.  Essentially this is the ``dns-nameservers`` entry that was defined in 
``/etc/network/interfaces`` when setting a fixed IP address.  If this entry is configured to use an external DNS such as Google, this will result in Shield being 
unable to resolve any internal names (e.g. server.company.local).  It is therefore important to ensure that this entry is configured to use an internal DNS server.  

DNS is also important between each server node. In other words, each server node will need to be able to resolve each of the other servers within the cluster. 
This can be achieved by ensuring that each node is registered with DNS, or by updating the host file on each machine.

Shield uses Subnet 10.42.0.0/16 & 10.43.0.0/16. In case the same range is already being used in the existing network, please contact Ericom Shield Professional Services.

**SSL & Firewalls**

It is **highly recommended** to disable any security agents running on the Shield servers, e.g. firewalls, SSL decryption etc.

		
Requirements for CDR Solution
=============================

Ericom Shield comes with a cloud-based file sanitization service for Evaluation purposes. It is also possible to use an on-premise factory 
integrated CDR solution. The requirements for an on premise file sanitization server ( must be a dedicated machine, either physical or virtual) are:

A Windows Server 2012R2 with the latest rollups and updates installed OR
A Windows Server 2016 with the latest updates installed - on a machine with:

*   16GB memory
*   4 core processors
*   100GB disk space 

For HA, it is recommended to have 2 dedicated CDR machines (supports up to 10,000 users)