****************************************
How To Install A Specific Shield Version
****************************************

It is possible to install a specific version of Shield. 

To discover which versions are available run::

    helm search -l shield

To install a specific version:

1. Retrieve the Shield Repository from the **specific** path (replacing the <VERSION> with the desired one, e.g. Rel-20.01.2)::

    curl -s -o add-shield-repo.sh https://raw.githubusercontent.com/EricomSoftwareLtd/Shield/<VERSION>/Kube/scripts/add-shield-repo.sh
    chmod +x add-shield-repo.sh
    ./add-shield-repo.sh -p <PASSWORD> 

2. Retrieve the deploy-shield.sh from the **specific** path (replacing the <VERSION> with the desired one, same as the above)::

    curl -s -o deploy-shield.sh https://raw.githubusercontent.com/EricomSoftwareLtd/Shield/<VERSION>/Kube/scripts/deploy-shield.sh
    chmod +x deploy-shield.sh
    ./deploy-shield.sh

For more details about these services, see `here <services.html>`_.