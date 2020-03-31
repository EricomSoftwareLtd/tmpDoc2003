***************
Shield Services
***************

Shield includes the following services:

*   `Install Shield <services.html#id1>`_

*   `Prepare Servers <services.html#id2>`_

*   `Add Shield Repository <services.html#id3>`_

*   `Deploy Shield <services.html#id4>`_

*   `Delete Shield <services.html#id5>`_

*   `Shield Support <status.html#collect-shield-information>`_


Please use these services as required during the different processes of installation, modifying an existing cluster, upgrading a version etc.

Install Shield
==============

This service is used to install shield.

Retrieve the install-shield.sh script::

    curl -s -o install-shield.sh https://raw.githubusercontent.com/EricomSoftwareLtd/Shield/Rel-19.12.1/Kube/scripts/install-shield.sh
    chmod +x install-shield.sh
    
Usage:: 

    sudo ./install-shield.sh -p <PASSWORD> [-l|--label] [-R|--ranchercli] [-f|--force]

Arguments::

    -p: Shield repository requires a valid **password**. Contact Ericom Shield Professional Services to get a valid password and replace it in the command.
    -l: Set Labels
    -R: Run the RancherCLI and create the cluster
    -f: Force Option

Prepare Servers
===============

This service prepares the server nodes before they can be joined into a cluster, e.g. configures the OS settings, 
installs docker etc. 

Retrieve the binary files::

    curl -s -L -o shield-prepare-servers https://github.com/EricomSoftwareLtd/Shield/releases/download/shield-prepare-servers-Rel-19.12.1/shield-prepare-servers
	chmod +x shield-prepare-servers
    sudo ./shield-prepare-servers [-u <USER>] <SERVERIPADDRESSES>

<SERVERIPADDRESSES> represents the IP addresses of the server nodes. Multiple IP addresses may be entered, separated by a space (" ").

E.g.::

    sudo ./shield-prepare-servers -u ericom xx.xx.xx.xx yy.yy.yy.yy zz.zz.zz.zz

.. note:: The Kernel may be updated during this process (if required).

Add Shield Repository
=====================

This service is used to retrieve Shield repository. 

Retrieve the add-shield-repo.sh script::

    curl -s -o add-shield-repo.sh  https://raw.githubusercontent.com/EricomSoftwareLtd/Shield/Rel-19.12.1/Kube/scripts/add-shield-repo.sh
    chmod +x add-shield-repo.sh
    
Usage:: 

    ./add-shield-repo.sh -p <PASSWORD> [-v|--version] <version-name> [-l|--list-versions] [-h|--help]

Arguments::

    -p: Shield repository requires a valid **password**. Contact Ericom Shield Professional Services to get a valid password and replace it in the command.
    -v: Install a specific version from repo (e.g. version-name = rel1911 will install the Rel-19.12.1 repository)
    -l: List all the available versions

Deploy Shield
=============

This service is used to start and run Shield. 

Retrieve the deploy-shield.sh script::

    curl -s -o deploy-shield.sh https://raw.githubusercontent.com/EricomSoftwareLtd/Shield/Rel-19.12.1/Kube/scripts/deploy-shield.sh
    chmod +x deploy-shield.sh

Usage::

    ./deploy-shield.sh [-n|--namespace <NAMESPACE>] [-l|--label] [-o|--overwrite] [-f|--force] [-h|--help]

Arguments::

    -n: Deploy a specific namespace: shield-management, shield-proxy, shield-farm, shield-elk
    -l: Set Labels
    -f: Force Option
    -o: Overwrite yaml files

Delete Shield
=============

This service is used to stop and remove Shield. 

Retrieve the delete-shield.sh script::

    curl -s -o delete-shield.sh https://raw.githubusercontent.com/EricomSoftwareLtd/Shield/Rel-19.12.1/Kube/scripts/delete-shield.sh
    chmod +x delete-shield.sh

Usage::

    ./delete-shield.sh [-n|--namespace <NAMESPACE>] [-s|--silent] [-k|--keep-namespace] [-h|--help]

Arguments::

    -n: Delete a specific namespace: shield-management, shield-proxy, shield-farm, shield-elk
    -s: Silent: do not ask for confirmation)
    -k: Skip deleting a specific namespace


