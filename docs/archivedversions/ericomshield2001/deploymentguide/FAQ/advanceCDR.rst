***********************************************************
How To Configure Advanced Features In Built-In CDR Solution
***********************************************************

Change Log Level
================

It is possible to change the logging level of the CDR solution. Default log level is **Debug**.

To do so, go to the following path on the CDR server: ``C:\Program Files\Votiro\SDS Web Service\Config``, and modify **logs.xml** file.

All log settings are defined in this file (e.g., LogLevel, MaxFileSize, NumberOfBackups etc.) and can be updated.

These settings are valid for each sanitization node. Same goes for the API and SNMC logs.

After updating the settings in the logs.xml, the SNMC and API services must be restarted on the CDR server.

Define Antivirus To Use
=======================

As of v8.3, if an AV license exists, there are 3 AV engines available to use: ESET, Avira & Windows Defender.
By default all of them are used consecutively.
To manually define which AV engine to use, navigate to "C:\Program Files\Votiro\Votiro.Malware.Scanner\Config\scanner.xml" 
and set the unnecessary antivirus engine to false::

        IsActivated="false" 

Enable HTTPS (SSL)
==================

An SSL certificate is used to establish a secure encrypted connection between a browser and a server.
An SSL certificate must be installed on the server and all browsers that connect to the CDR using HTTPS. 
You must have administrator privileges on the CDR server and access to the Windows SDK to use the file ``makecert.exe``. 
The process involves generating and installing an SSL certificate. If you already have an SSL certificate, skip to step2. 

1. Create and install a certificate on the CDR server: 

*   Create a ROOT certificate by issuing the following command::
        
        makecert.exe -sk RootCA -sky signature -pe -n CN=<MachineHostName> -r -sr LocalMachine -ss Root <RootCertName>.cer 

*   Create a server certificate::

        makecert.exe -sk server -sky exchange -pe-n CN=<CDRServerIpAddress> -ir LocalMachine -isRoot -ic <RootCertName>.cer -sr LocalMachine -ss My <CertName>.cer
        
*   Browse to the Windows Certificate list and verify that a new valid certificate exists under the Personal path.

*   Copy the server certificate’s Thumbprint under Details > Thumbprint.

*   Bind the server certificate to your SSL port (default: 443) with the following command::

        netsh http add sslcert ipport=0.0.0.0:443 certhash=<thumbprint> appid={b6445322-3509-4d0f-8b4b-0a12eeadaed0}

2.  Restart the Votiro.Sanitization.API and Votiro.SNMC Windows services.

3.  Browse to **https://CDRServerIPAddress/SDSService/v3**. Verify that there is no certificate warning or validation issue.

Download Big Files
==================

In the Shield built-in CDR solution there is a known limitation for file size. Maximum size allowed for sanitization is 2.1 GB.

In order to allow larger files, follow these steps:

1. Go to ``C:\Program Files\Votiro\SDS Web Service`` 

2. Edit ``SdsApiService.exe.config`` file: increase the **maxReceivedMessageSize** under ``WEBHttpBinding_ISdsWebService`` and ``WEBSecureHttpBinding_ISdsWebService`` to the desired size (in bytes)

3. Go to ``C:\Program Files\Votiro\SDS Web Service\config``

4. Edit ``machine.xml`` file: under ``SystemSettings`` add **MaxInProcessSizeInBytes=”5368709120”** with the same size you entered in step 2.

5. Restart both services – ``Votiro.Sanitization.API`` and ``Votiro.SNMC``.

Update User Displayed Message
=============================

For archived folders, when the included files are blocked (by the CDR process), they are replaced with a pdf document to inform the user that the item has been blocked. 
It is possible to change the message displayed to the user by updating the dictionary template located on the CDR server.

The dictionary templates are located in ``C:\Program files\Votiro\SDS Web Service\Templates\Blocked``

After updating the dictionary templates, the SNMC and API services must be restarted on the CDR server.