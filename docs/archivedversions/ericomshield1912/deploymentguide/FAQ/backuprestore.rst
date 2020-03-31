******************************
How To Backup & Restore Shield
******************************

Backup
======

Using Remote Backup
-------------------

Shield supports SFTP as a remote storage for backup files. Follow theses steps to define the backup settings in the system.

Create a dedicated account for this purpose. This account will be used to store the backup files and also to retrieve these files when restoring Shield. 

On the SFTP server, create a SSH key. For more details, see `here <SSHKeys.html>`_.

On the Rancher Server machine, download the custom-management file to the **ericomshield** folder::

        curl -s -o custom-management.yaml https://raw.githubusercontent.com/EricomSoftwareLtd/Shield/Rel-19.12.1/Kube/scripts/custom-management.yaml

Edit the file to configure the SFTP account (backup path, SFTP server IP & username) and copy the SSH private key. 
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

Save the changes and deploy Shield, run::

    ./deploy-shield.sh

.. note:: When editing the yaml file it is important to avoid any redundant characters (e.g. blank spaces, tabs etc.). In addition, it is recommended to back up this file.

Using Local Backup
------------------

Backup files may be stored locally on Shield machines. 
On a single machine system, if the node is down - the backup will be lost.
On a multi machine system, several backups may exist on the different machines and it is hard to tell which 
backup should be used in case a restore is needed. Using the local backup **as is** is not recommended and the best 
practice is to update the backup path to a specific folder, this way everytime a new backup file is created - 
this folder will contain the most recent backup file. 

The recommendation is to use a NFS folder or another local folder which is backed up on a **regular** basis.

To update the local backup path, follow these steps:

On the Rancher Server machine, download the custom-management file to the **ericomshield** folder::

    curl -s -o custom-management.yaml https://raw.githubusercontent.com/EricomSoftwareLtd/Shield/Rel-19.12.1/Kube/scripts/custom-management.yaml

Edit the file to update the local backup path. Uncomment the **localPath** variable and set it to the designated path::

    localPath: <SPECIFIC_FOLDER_PATH>

Save the changes and deploy Shield, run::

    ./deploy-shield.sh

.. note:: When editing the yaml file it is important to avoid any redundant characters (e.g. blank spaces, tabs etc.). In addition, it is recommended to back up this file.

Additional Backup
=================

It is highly recommended to backup the Rancher Store, the yaml files and the .kube/config on a **regular** basis. These backups can be 
used in the case of Rancher Server failure. 

To do so, backup the ``~/ericomshield/`` and the ``~/.kube/config`` folders on the **Rancher Server** machine.

Restore
=======

Restore is performed automatically when required (e.g. system failure).

To perform a manual restore using a specific backup file, follow these steps:

In the Administration Console, go to ``Settings | Restore``

Select and upload a file to restore and click the ``Restore Shield`` option. 

For more info, please see `here <../Admin/settings.html#restore>`_.