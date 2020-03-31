******************************************************
How To Migrate From Legacy Mode To Shield (Kubernetes)
******************************************************

To migrate existing legacy systems to Shield running on Kubernetes, please follow these steps:

.. note:: For any help in this process, please contact Ericom Shield Professional Services.

1.  Backup the legacy system. Modify something in the administration console (this will create a new backup file) or use the latest daily 
    backup file from the /usr/local/ericomshield/backup/daily

2.  Shield supports SFTP as a remote storage for backups and uses it for restoring purposes. 
    Create a dedicated account for this purpose. The required details are the server IP and username. 

3.  Place the backup file (from the legacy system) under the SFTP account

4.  On the SFTP server, create a SSH key. For more details about SSH keys go `here <SSHKeys.html>`_.

5.  Create a new Shield system. Form a new Shield Kubernetes cluster as described in `here <../deployment.html>`_. 
    Additional steps are required prior to deploying Shield, so stop before deploying it.
    
6.  On the Master machine, download the custom-management file to the current folder::

        curl -s -o custom-management.yaml https://raw.githubusercontent.com/EricomSoftwareLtd/Shield/Rel-20.01.2/Kube/scripts/custom-management.yaml

7.  Edit the file to configure the SFTP account (path, IP & username) and copy the SSH private key. 
    (Missing settings are marked with ``<>``)::

	    remotePath: "<BACKUP_PATH>"
	    config: |
	      rclone.conf: |
	        [SFTPStorage]
	        type = sftp
            host = <SFTP_SERVER_IP>
            user = <SFTP_USERNAME>
            key_file = /keys/key_file.pem
	    key: |
            key_file.pem: |
            ----BEGIN RSA PRIVATE KEY-----
            <PRIVATE_KEY>
            ----END RSA PRIVATE KEY-----

8.  Continue with the deployment instructions. The deployment will refer to the updated custom-management file. Go `here <../deployment.html#deploy-shield>`_.
        
9.	Use Shield in the new, Kubernetes deployment.
