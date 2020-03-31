*****************
Sasa Gate Scanner
*****************

Ericom Shield can integrate with Sasa Gate Scanner CDR solution.

For Shield to integrate with this CDR solution, it needs to be defined in the Administration Console with all relevant settings filled in.

For more details about configuring this solution in the Admin, please go `here <../deploymentguide/Admin/settings.html#sasa-gate-scanner>`_.

It is possible to use this solution with the default named policy mapped to Shield or define additional named policies.

For more information about defining named policies in Shield, go `here <../deploymentguide/FAQ/namedpolicies.html>`_.

The default Sasa named policy includes the use of 5 different anti-viruses, which are used consecutively. Downloading a file includes these scanning mechanisms and may take a while to complete.

This can be modified using the Sasa MaM console.

.. note:: If the mapped named policy does not match an existing policy in Sasa MaM console, then the Sasa default named policy will be used. The user will not be informed about the actual policy that was used. This information can only be visible in the **Sanitized** report.
