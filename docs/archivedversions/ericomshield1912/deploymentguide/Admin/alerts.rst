******
Alerts
******

Ericom Shield includes a notifications and alerts mechanism. For details see `here <dashboard.html#notifications-and-alerts>`_.

These alerts can be sent to users using several methods, e.g.: Slack, emails or POST requests.

System statistics and end user feedback can also be sent, using the same methods.

.. note:: System statistics are sent once every 24 hours. Alerts and end user feedback are sent simultaneously, as they are issued.

In this section of the administration console, it is possible to define the required settings for each of these methods. Multiple methods can be defined simultaneously. 


Slack
=====

Alerts and statistics can be sent using the **Slack** method. If new to **Slack**, please go `here <https://slack.com/>`_. 

**Slack** can be used in two different channels:

*   Webhooks - for details on defining a webhook, go `here <https://api.slack.com/incoming-webhooks>`_.

    Shield supports webhooks for alerts, statistics and end user feedback. Define the matching webhook URL to start receiving this information from Shield. The **same** webhook can be used for all fields, if desired.

*   OAuth - for details on defining OAuth, go `here <https://api.slack.com/docs/oauth>`_. 

    When working with OAuth, define a token that matches the different channels (available for alerts, statistics and end user feedback.)

Email
=====

Define a SMTP server to send alerts, statistics and end user feedback. Required settings are: Host, Port, whether to use securely of not and Credentials.

.. note:: SMTP server does not support connecting with 2 Factor Authentication.  

Please also define the account name that sends the alerts, and a group account to receive the alerts.  Multiple email addresses can be defined, seperated by a semicolon (";").

It is also possible to define a specific subject text for each option (alerts, statistics and end user feedback), which makes filtering all received emails easier (as these might accumulate in time).

POST
====

Alerts, statistics and end user feedback can be sent to any Web Service that supports POST requests. 
Define matching URLs for the desired options, and the relevant information will be sent from Shield to these URLs. The **same** URL can be used for all fields, if desired.

Send Test Alert
===============

To verify that all desired alert channels are properly defined, fill in details and select the ``Send`` option. 
A test alert is sent (to all defined channels). If this alert was not received correctly, this is due to incorrect settings. Update settings and try again.

List Of Alerts
==============

Here is the list of alerts that can be found in the Shield Administration Console:

*   There are no available user licenses

*   There are no available session licenses

*   Users licenses are about to run out (**NumOfLicenses** in use)

*   Session licenses are about to run out (**NumOfLicenses** in use)

*   License expiration date has passed

*   License will expire on **LicenseExpirationDate**

*   Your system requires activation

*   The system is approaching its maximum Remote Browsers capacity on the following Dynamic Nodes Farm URLs: **FarmInfo**

*   The system has reached its maximum Remote Browsers capacity on the following Dynamic Nodes Farm URLs: **FarmInfo**

*   Failed contacting the following Dynamic Nodes Farm URLs: **FarmInfo**

*   Browsers Farm CPU Usage is **CpuUsage** and potentially overloaded

*   Browsers Farm Disk Usage is **DiskUsage** and potentially overloaded

*   Browsers Farm Memory Usage is **MemoryUsage** and potentially overloaded

*   The following nodes are not in the 'Ready' state: **NodesList**

*   CPU Usage is potentially overloaded on the following nodes: **NodesList**

*   Disk Usage is potentially overloaded on the following nodes: **NodesList**

*   Memory Usage is potentially overloaded on the following nodes: **NodesList**

*   Authentication Settings Errors (specifying the incorrect setting)

*   Failed contacting Sanitization Server on the following Dynamic Nodes Farm URLs: **FarmInfo**

*   Votiro Cloud Evaluation version cannot be used in a production deployment. It is being used on the following Dynamic Nodes Farm URLs: **FarmInfo**

*   No matching license for the selected CDR provider (**CDRProviderName**)

*   Antivirus scan is not included under the current license terms. Please purchase a matching license

*   Failed to contact Categories Provider Server on the following Dynamic Nodes Farm URLs: **FarmInfo**

*   Some replicas of the following services are not running: **ServicesList**

*   There are currently no standby remote browsers

*   DNS Settings are not complete. Fill in at least one internal and one external DNS address under **Settings | DNS**

*   Administration Console FQDN not set. To use the administration console in a secure manner, fill in FQDN under **Settings | SSL**

*   Some users are associated with several Active Directory groups, therefore, relate to several Shield profiles.
    This may lead to inconsistent Shield Policies enforcement. It is recommended for each user to be part of a single Shield group.

