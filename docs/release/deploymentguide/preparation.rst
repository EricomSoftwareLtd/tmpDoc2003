*******************
Machine Preparation
*******************

As stated in the `Requirements <requirements.html#software-requirements>`, all machines in the Shield system should have:

*   A fixed IP Address
*   A unique hostname
*   The same timezone (as other machines in the system)

Please follow these steps to prepare the machines:

1.  Login using: **ericom/ericomshield**

2.  Configure the IP of the machine to be unique and **static**:

	*	Go to /etc/systemd/network

	*	Edit the 20-wired.network file. Change the line with **DHCP=ipv4** to refer to a specific IP address/subnet, for example::

			[Match]
			Name=en*
	
			[Network]
			Address=10.1.10.12/24
			Gateway=10.1.10.1
			DNS=10.1.10.1
			DNS=10.1.10.2 	//optional, multiples may be used
			IPForward=ipv4

.. note:: In case a DHCP server exists in the environment, configure it to lease a reserved (static) IP to the OVA. You should be able to determine the MAC address of the OVA by the IP address given the OVA at first startup.

3.  All the machines should be synchronized. Configure the NTP (Network Time Protocol) and the timezone on the machine::

		sudo timedatectl set-ntp on
		sudo systemctl restart systemd-timesyncd
		timedatectl set-timezone <Continent>/<City>

4.	Rename the machine with a **unique** name (necessary for the cluster to be created properly). As **root**, run::

		hostnamectl set-hostname <NewUniqueHostname>

5.  Update the new hostname in the ``/etc/hosts`` file. If it is missing - add it.

6.  In case the Shield system will include an **Upstream Proxy which uses SSL Inspection**, a matching certificate must be installed on the machine. To do that, create a file **cert-1.crt** under ``/usr/local/share/ca-certificate/cert-1.crt`` and run::

        sudo update-ca-certificate

7.  Reboot the machine

Repeat these steps for **EACH** machine in the system.