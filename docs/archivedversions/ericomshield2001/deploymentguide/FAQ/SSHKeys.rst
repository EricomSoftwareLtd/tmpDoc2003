**********************
How To Set Up SSH Keys
**********************

Using SSH keys is much safer. Most cloud providers are working with SSH keys, meaning using certificates (that include public and private keys), to connect to machines. Shield supports connecting using certificate. In order to enable connection using certificate, create the certificate (public and private keys) and copy the public key to the machine that is about to be connected. 

Create the SSH Public and Private Keys
======================================

*   Run as user ericom (not root)::

        sudo ssh-keygen -t rsa

*   Enter file name in which to save the key (e.g., ./shield)

*   Enter passphrase (password for the certificate for additional security. Optional. Empty for no passphrase)

*	Two files are created. E.g., shield.pub (the public key) and shield (the private key). Verify in the files that the user name is ericom (not root).

Copy Public Key to Target Machine
=================================

*	In the root of the target machine, make sure a folder named ``.ssh`` exists. If there is no such folder, create it.

*   Copy the public key to a file named ``authorized_keys`` and place it in the ``.ssh`` folder.

*	Log into the target machine using::

            ssh -I shield username@IPAddress
        
    Verify that no password is required, that a ``.ssh`` folder exists and that it includes a ``authorized_keys`` file in it folder.

*	If a passphrase is defined – enter it to log in.
