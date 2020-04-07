*******************
Opswat MetaDefender
*******************

Ericom Shield can integrate with Opswat MetaDefender CDR solution.

For Shield to integrate with this CDR solution, it needs to be defined in the Administration Console with all relevant settings filled in.

For more details about configuring this solution in the Admin, please go `here <../deploymentguide/Admin/settings.html#opswat-metadefender>`_.

Please note that there is no build-in default policy. A specific rule (created in Opswat UI) must be mapped. 
Edit the default entry, and set the external rule name in the Provider Named Policy column. For more information about defining named policies in Shield, go `here <../deploymentguide/FAQ/namedpolicies.html>`_.


.. note:: If the mapped named policy does not match an existing policy in Opswat console, an internal error will be issued and the exact reason is available in the matching report in the Shield Admin UI
