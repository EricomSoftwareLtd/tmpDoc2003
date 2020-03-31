*****************
File Sanitization
*****************

Ericom Shield is supplied with a fully integrated CDR solution at no extra cost. 

Ericom Shield supports other CDR solutions that can be integrated in the system, according to customer's requirements. For more details, go `here <../CDR/providers.html>`_. 

For High Availability purposes it is possible to map Shield to 2 CDR servers (primary and secondary). If the primary fails, the secondary will be used.

In order to use the integrated CDR solution, the following actions are required:

*     Install the file sanitization server on a dedicated Windows Server according to the following `instructions <../CDR/installationinstructions.html>`_. 

*     In the Administration Console, fill in the Primary File Sanitization URL with the following URL **http://CDRServerIPAddress/SDSService/v3** 

*     Fill in the Secondary Secondary File Sanitization URL

Where the ``CDRServerIpAddress`` is the above mentioned Windows Server.

Within the Shield Administration console, it is possible to configure how the CDR engine will process files. For more details, see section `Files and Sanitization <../deploymentguide/Admin/settings.html#files-and-sanitization>`_. 

.. note:: The built-in CDR solution comes with a 30 days trail period. Once this trail period is complete it is essential to obtain a license. For more details on this matter please contact Ericom Shield Professional Services.

Additional Info
===============

1. The CDR provider supports various file types. Here is a list of the most common and often used file type (note that this list is not complete and may be changed by the CDR provider):

    doc, docx, docm, xls, xlsx, xltx, xlsm, ppt, pptx, pptm, dot, dotx, dotm, xlsb, pps, ppsx, pot, potx, pdf, jpeg, jpg, gif, tif, tiff, png, bmp, bin, txt, bat, css, html, xml, dwg, cad, rft, tar, jar, gzip, 7z, zip etc. 

2. To configure certain additional advanced features, go `here <../deploymentguide/FAQ/advanceCDR.html>`_.

