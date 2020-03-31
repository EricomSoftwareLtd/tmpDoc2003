Safari/Mac
==========
After downloading the certificate, go to “Finder” and the bottom left, and select “Applications | Utilities | Keychain Access”. 

.. figure:: images/KeyChainAccess.png
	:scale: 55%
	:align: center
	
Double click it to open. 

.. figure:: images/UnlockKeyChain.png
	:scale: 75%
	:align: center
	
Right-click the “System” and select “Unlock Keychain "System" ”. Once unlocked, go to “File | Import Items” and find the downloaded certificate. Select it and click “Add”. The certificate is now added to the keychain. Select the “ericom.com” certificate and double click it. 

.. figure:: images/AlwaysTrust.png
	:scale: 75%
	:align: center
	
Make sure all the fields are marked with “Always Trust” - set the first line to this value and the other lines will be updated. Once done, right-click the “System” and select “Lock Keychain "System" ”.