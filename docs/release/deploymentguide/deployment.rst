*************************
Installation & Deployment
*************************

Shield can be installed in 2 main methods, using the **Installation Scripts** (suitable for Ubuntu and CentOS) and using the **OVA file** (suitable for Ubuntu).

Shield components are deployed on Linux machines using Rancher. Rancher is a well-known software platform that enables easy 
deployment and management of Docker and Kubernetes products in production environments.

The recommendation is to set up a dedicated Linux machine which will be used for cluster deployment and management. This machine 
will be referred to as the **Rancher Server** machine. This machine will include all the internal components (e.g. Kubectl & Helm). 
The **Rancher Server** can be a separated machine or on one of the Master machines (running etcd & Control Plane).

For High Availability deployments (recommended), 3 Master (cluster management) machines are required.

When installing using the **OVA**, some steps can be skipped (due to the components that are included in the OVA). 
For detailed instructions on installing using the OVA go to:

*	`Installation Scripts <installation.html>`_

*	`OVA Installation <deploymentova.html>`_

