*********************
Kerberos Instructions
*********************

Each Shield system must have a dedicated user account created especially, to allow authenticating domain users via Kerberos.

This dedicated user should have a password that never expires and should skip the Kerberos pre-authentication mechanism.

Follow these steps to create the user:

*	On a Domain Controller open ``Active Directory Users and Computers``

* 	Select **Action | New | User** from the menu

* 	Enter the details for the new user account and click ``Next``

* 	Set the desired password, ensure that "User must change password at next login" is **not** checked and check "Password never expires".

*  	After saving the user, re-open and select the ``Account`` tab, set "Do not require Kerberos pre-authentication" in the ``Account options section``.

Once the user is created, a Keytab file needs to be generated. Keytab files contain a shared secret that allows a none windows machine (in this case the Shield Server) to utilize Kerberos. To create a keytab file:

*   Open command prompt on the Domain Controller.

*   Create a keytab and map the username to the new service name (use the user credentials previously created), using the command copied from the Kerberos settings in the admin (more details `here <../deploymentguide/Admin/profiles.html#keytab>`_) or using the following command::

        ktpass -out <DNS Name>.keytab -mapUser <Full UPN of User> -pass <Password> -mapOp set +DumpSalt -crypto rc4-hmac-nt -ptype KRB5_NT_PRINCIPAL -princ HTTP/<FQDN of Shield Server>@<DOMAIN>
    
    **A Working Example:**

    User: shield@company.local

    Password: Password1

    Shield Server: HTTP/Shieldnode.company.local@COMPANY.LOCAL

    Taking the details provided above as an example, the command used to create a keytab file would be as follows::

        ktpass -out Shieldnode.company.local.keytab -mapUser shield@company.local -pass Password1 -mapOp set +DumpSalt -crypto rc4-hmac-nt -ptype KRB5_NT_PRINCIPAL -princ HTTP/Shieldnode.company.local@COMPANY.LOCAL

    .. note:: It's important for Kerberos authentication that uppercase is used for the domain name (HTTP/Shieldnode.company.local@COMPANY.LOCAL).  And also when configuring the browser to use the Shield server as the proxy, it's important to also use the FQDN rather than the IP address. 



    More information about creating a Keytab file can be found `here. <https://technet.microsoft.com/en-us/library/cc753771(v=ws.11).aspx>`_