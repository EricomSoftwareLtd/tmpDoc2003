*********************************
Install Shield Using OVA - Online
*********************************

Create The Server Machines
==========================

1.	From the VMware vSphere client, select ``File > Deploy From OVF Template``. 

.. figure:: images/ova1.png	
	:scale: 75%
	:align: center

Browse to the location of the OVA file and select it. Click ``Next``

.. figure:: images/ova2.png	
	:scale: 50%
	:align: center

.. figure:: images/ova3.png	
	:scale: 50%
	:align: center

2.	Name the file and select the storage path. Complete all the steps and click ``Finish``

.. figure:: images/ova4.png	
	:scale: 50%
	:align: center

.. figure:: images/ova5.png	
	:scale: 50%
	:align: center

3.	Wait for the machine to be ready

.. figure:: images/ova6.png	
	:scale: 75%
	:align: center

4.	Enter the machines settings and change the CPU to 8 cores (minimum) or 12 cores (recommended) and the memory to 16GB (minimum).

.. figure:: images/ova7.png	
	:scale: 55%
	:align: center

5.	Power on the machine.

.. figure:: images/ova8.png	
	:scale: 75%
	:align: center

6.	Follow the steps detailed in `Machine Preparation <preparation.html>`_

7.	If required, increase the size of the OS (to match the VMware size). Run::

		growpart /dev/sda1
		resize2fs /dev/sda1

Prepare The Rancher Server
==========================

.. note:: Shield repository requires a valid **PASSWORD**. Before you continue, contact Ericom Shield Professional Services to get a valid password.

On the Linux **Rancher Server** machine, run this service:: 

	sudo ./install-shield.sh -R -l -p <PASSWORD>

This command will run Rancher (-R) with all the labels (-l) and use the latest (online) Shield repository.

Now that all the Server Machines are ready, continue with the installation steps detailed `here <installation.html#connect-the-server-nodes-to-the-cluster-master>`_.