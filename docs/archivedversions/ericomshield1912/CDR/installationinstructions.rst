****************************************
Installation Instructions for CDR Server
****************************************

Prerequisites
=============

A dedicated Windows Server with the following `specifications <../deploymentguide/requirements.html#requirements-for-cdr-solution>`_.
This server IP address is referred to as ``CDRServerIpAddress``

*   When installing on Windows Server 2012R2, .NET versions 4.5.2 and 4.6 are required. 
    To do so, run **full Windows Updates** procedure on the server, or install these versions manually.

*   When installing on Windows Server 2016 and up, several .NET 3.5 features are required. 
    To do so, run **full Windows Updates** procedure on the server, or install these components manually:
    
    *   Internet Information Services
    
    *   .NET Extensibility 3.5
    
    *   Message Queuing

    *   SNMP WMI Provider
    
    *   Windows Powershell 2.0 Engine

    *   Visual C++ Redistributable Packages for Visual Studio 2008 (32-bit and 64-bit)

Deployment
==========

Shield Versions & Recommended CDR Versions
------------------------------------------

    .. csv-table::
        :header: "Shield Verion", "CDR Version"
        :widths: 10, 10

        Rel-19.12/Rel-19.11/Rel-19.09.5, `v8.3 <https://download.ericom.com/public/folder/NKVCccudNkej3xGcJj3KUg/8.3>`_
          
    
*   Go to the selected version download folder and download **all** files locally.

*   Run and install all packages included in the installation. Click ``Next`` until installation is complete.

*   Verify that the Windows Service named **Votiro SDS WebService** is installed and that the service is running (in **Running** state).

*   To enable Password Protected files support, save the previously downloaded **PasswordPolicy.xml** locally (under ``C:\Program Files\Votiro\SDS Web Service\Policy``).

*   Save the previously downloaded **Blocked.rtf** file locally (under ``C:\Program Files\Votiro\SDS Web Service\Templates\Blocked``).

*   To avoid realtime antivirus (AV) scanning issues, it is recommended to exclude the CDR folders from the AV software (on the CDR server itself). E.g., for **Windows Defender**, add an exclusion for the CDR folder:

    .. figure:: images/AVexclusion.png
        :scale: 50%
        :align: center

    If another AV software is used, configure this exclusion as per the specific AV.

*   Use the CDR Server IP address (``CDRServerIpAddress``) in the Ericom Shield Administration Console.

