*********
Resources
*********

Ericom Shield includes smart resources management. To optimize system resources, Ericom Shield detects user activity and frees up resources.

Shield includes several timeouts. The purpose of these timeouts is to maintain Shield resources usage as low as possible, by releasing un used, idle sessions (and their related containers). 
To manage un-used sessions there are 3 timeouts categories: suspend, terminate and absolute.

**Suspend** timeouts - these are short-term timeouts. Managed via the Suspend Tabs field and are separated for Read-Only and Read-Write tabs. Managed also via the policies table (can be defined in the system level, or per specific domain).
The recommendation for these timeouts is to keep them relatively short (up to an hour), while Read-Only is the shortest and Read-Write is longer (to preserve written input longer).

**Terminate** timeouts - these are longer-term timeouts. Relevant for all tabs, either Read-Only, Read-Write, background or foreground. These timeouts relate to the state of the system, whether it is overloaded or not. 
These timeouts should be defined with greater values than the Suspend timeouts and circle around the several hours.

**Absolute** timeout (Maximum Remote Browser Session) – this timeout is the absolute limit, for all tabs and system states. This timeout is recommended as a daily timeout, to make sure no un-used sessions remain active at the end of the workday.

Resources Settings are arranged in the following sub-sections:


Session Management
==================

Minimum Standby Remote Browser Sessions
---------------------------------------

Represents the minimum number of standby remote browsers in the system. 
CPU and memory are constantly monitored, throughout the system. 
According to these inputs, the number of standby browsers is calculated (in accordance with the Maximum Capacity Threshold). If the admin user chooses to populate this field 
manually, Shield system will have the desired number of standby browsers ready for use, regardless of the system’s maximum capacity. This might cause system overload, so needs 
to be considered carefully. To return to system defined value, delete the field and save the settings – and the system defined values will be recalculated and displayed.

Dynamic Standby Remote Browser Sessions (%)
-------------------------------------------

This setting is available only when the system is in **Dynamic Mode**. Define the desired percentage of standby remote browsers sessions. 
Calculated dynamically based on the number of **currently** active browsers, to ensure browsers availability at all times. 
The higher value of the two settings (this and ``Minimum Standby Remote Browser Sessions``) will be used.

For example::
    
    if a system has 100 Active browsers and 
    Minimum Standby Remote Browser Sessions = 10 
    Dynamic Standby Remote Browser Sessions (%) = 15 


    There will be 15 standby available browsers in the system.

Standard Terminate Session Timeout (min)
----------------------------------------

Define the time for browsing sessions to remain alive when no user activity is detected (in minutes). Will take an effect when **Suspend Tab Timeouts** (R/O or R/W) are set to 0 or when **Suspend Tabs** is set to None.
When this timeout is met, the session is terminated. If this is a foreground tab - user receives a matching message and should refresh the page to reload it. 
If this is a background tab, upon re-opening it, the tab is refreshed.
 
Maximum Remote Browser Session Duration (min)
---------------------------------------------

Sets the **absolute** session timeout for each browser session (in minutes). When this timeout is met, regardless of activity, the session is terminated to free up resources. If this is a foreground tab - user receives a matching message and should refresh the page to reload it. If this is a background tab, upon re-opening it, the tab is refreshed.


Resources Conservation
======================

Maximum Active Remote Sessions Per User
---------------------------------------

Define the maximum number of **active** remote sessions (tabs/applications) a user may have. This number does not include suspended tabs. Used in order to prevent DDOS attacks and to maximize system resources. If this number is reached and the user wants to open a new tab - one of the opened tabs must be closed first.

.. note:: A user is defined by User Authentication, IP address or using XFF. 

Rate Limiter Excluded IP Addresses
----------------------------------

Shield includes a connections rate limiter, to protect from DDOS attacks. To disable this limiter for specific IP addresses, define the addresses to exclude (multiple values can be defined, separated by a comma \",\"). The value can be IP address or subnet. E.g. 126.0.2.50 for a single IP address or 126.0.1.1/16 for a subnet.

.. note:: Setting it to 0.0.0.0/0.0.0.0 will disable the rate limiter completely (not-secure).
   
Resources Saver Timeout (min)
-----------------------------

Define the time for a foreground idle tab to remain fully active. When this timeout is met, the consumed resources are lowered substantially. 

Suspend Tabs
------------

Define the idle tabs suspension policy. Possible values: Both, Foreground, Background and None. The recommendation (and default value) is Both, since any other option consumes system resources and might require additional hardware.

Idle tabs (foreground, background or both) will be suspended according to the relevant Suspend Tab Timeout (whether they were read-only or read-write).

If **None** is selected, the tabs will remain alive until Terminate Timeouts are met.

Suspend R/O Tab Timeout (min)
-----------------------------

Define the time for a read-only tab (foreground, background or both) to remain alive while idle (in minutes). A read-only tab is a tab that has been used only for reading. When this timeout is met, the tab is suspended to free up hardware resources. When the tab is reactivated, it is refreshed (either manually/automatically) to display latest content. Setting it to 0 will disable the feature and the idle tab will remain alive until the Standard Idle Timeout is met. Default is 5 min.

Suspend R/W Tab Timeout (min)
-----------------------------

Define the time for a read-write tab (foreground, background or both) to remain alive while idle (in minutes). A read-write tab is a tab where the user wrote on it (e.g. filled a form on it). 
When this timeout is met, the tab is suspended to free up hardware resources. When the tab is reactivated, it is refreshed (either manually/automatically) to display latest content. 
Written input will be retrieved as per the specific domain behavior (some sites auto save input and others do not, in this case input is lost). 
Setting it to 0 will disable the feature and the idle tab will remain alive until the Standard Idle Timeout is met. Default is 30 min. It is recommended that this timeout is greater than the R/O timeout, to help maintain the written input from getting lost.



Load Management
===============

Maximum Capacity Threshold (%)
------------------------------

Defines the maximum capacity threshold in % terms. When the resources usage (CPU or memory) reaches this threshold, no additional remote browsers will be allocated, until capacity threshold drops. 

In order to increase security and resource utilization, shield will disconnect idle sessions. When the system is not loaded, the idle timeout is set to the standard timeout value (i.e. default 8 hours), when the system is loaded the idle timeout is set to the ``Load Idle Timeout``.

Maximum Load Threshold (%)
--------------------------

Defines the maximum load threshold of browsers 'in use', in % terms. Once this value is reached, is considered overloaded and will use the Load Idle Timeout. This will cause unused browser sessions to be released more frequently, thus maintaining system resources in an optimal state.

Minimum Load Threshold (%)
--------------------------

Defined the minimum capacity threshold of browsers ‘in use’, in % terms. Once this value is reached, the Standard Idle Timeout is used, or the Background Tab Timeout fields, if defined.

Load Terminate Session Timeout (min)
------------------------------------

Define the time for browsing sessions to remain alive when no user activity is detected during system overload (in minutes). Will take an effect when **Suspend Tab Timeouts** (R/O or R/W) are set to 0 or when **Suspend Tabs** is set to None. 
Relevant **only** when the system is considered **overloaded**. When this timeout is met, the session is terminated. If this is a foreground tab - user receives a matching message and should refresh the page to reload it. If this is a background tab, upon re-opening it, the tab is refreshed.

Burst Events
============

This subsection is relevant in **Dynamic Mode** only. Allows to define Burst Events in the system, when at a given day and time, a predefined number of remote browsers will be available to be used. This ensures that at these predefined periods of time, enough remote browsers are ready and available in the system for immediate use.

Enable Burst Events
-------------------

Enable or disable the Burst Events. If set to No, any events defined in the system are ignored and browsers are managed regularly in the system (disregarding peak hours). 

Burst Events Table
------------------

Add, edit or delete burst events. 
Burst events should be planned to match the peak hours usage in the system. Create new events using the ``Add Burst Event`` dialog. Different events may be created, to match weekdays, weekends and several peaks along the day. Fill in the time of day, the days of the week, the number of required browsers and the timeout (in minutes), to be used for idle browsers. 
Once an event is created per a certain time of day, no more **new** events may be defined for that same time. It is possible to edit this entry directly in the table.
Edit any entry in the table by selecting the row and modifying each cell as desired. Make sure the time value is unique. 
In case of duplications - a message is displayed, allowing the user to edit the changes.

In addition, it is important to set the timeout for the idle browsers, to avoid loading the system. If no timeout is defined, the Standard Terminate Session Timeout will be used. 

.. note:: At these events, there is a possibility that the system will be close to, or indeed, overloaded. Defining the events should be done after careful consideration of the system capacity, the expected usage and the users needs.

Bandwidth Consumption
=====================

This sub-section includes settings related to the bandwidth consumption, to help administer the Fair Usage Policy. Each session has a limited bandwidth size, and when this bandwidth is consumed the session is terminated. It is possible to define a warning level and an error level, to update the end user about the current bandwidth usage and allow to save the work prior to session termination.

Max Bandwidth (GB)
------------------

Define the maximum bandwidth allowed (per session).

Warning Level (%)
-----------------

Define the level of used bandwidth to issue a warning to the user. Once met, the user is notified about the current bandwidth usage.

Error Level (%) 
---------------

Define the level of used bandwidth to issue an error to the user. Once met, the user is notified about the current bandwidth usage and warned about impending session termination. Soon after that the session is terminated since the allowed bandwidth was consumed.

Display Settings
================

This sub-section includes settings related to the display quality. The settings have recommended system default values, calculated in order to provide the best display while maintaining resource consumption.
It is not recommended to change these settings and in case these settings are updated - these updates might seriously affect system resources and bandwidth consumption. 
Please consult with Ericom Shield Professional Services before making any changes to these settings.

.. note:: To return to system defaults, simply delete the updated value and save. System default value will be restored. Related to ALL below mentioned settings. To restore entire sub-section settings - use the ``Restore System Defined Values`` option at the bottom.

Initial FPS Limit
-----------------

Define the maximum FPS rate limit when the page is opened. 

Media FPS Limit
---------------

Define the maximum FPS rate limit when a media element (non-FMS) is playing in the page. 

Non-Media FPS Limit
-------------------

Define the maximum FPS rate limit when the page includes only non-media elements (or when a media element stops). 

Scroll FPS Limit
----------------

Define the maximum FPS rate limit upon scrolling. 

Compression Quality For Media Elements
--------------------------------------

Define the quality compression rate for media elements in a mixed page (which includes media & non-media elements in it). 

Compression Quality For Non-Media Elements
------------------------------------------

Define the quality compression rate for non-media elements in a mixed page (which includes media & non-media elements in it). 

Enable High Quality For Non-Media Elements
------------------------------------------

Enable high quality text display in non-media elements. When enabled, text display in non-media elements is improved automatically and in addition, the following 
field (**Quality For Text Display**) is effective.

Quality For Text Display 
------------------------

The quality compression rate for text display. The higher the value, the darker and bolder the text display. Effective only when the **Enable High Quality For Non-Media Elements** is set to Yes.

Compression Quality Upon Idle
-----------------------------

Define the quality compression rate when no updates are received in the page (idle state). Changes may be due to scrolling, media playing, internal site updates etc. 

Compression Quality Upon Scroll
-------------------------------

Define the quality compression rate upon scrolling. 

Compression Quality During High FPS Rate
----------------------------------------

Define the quality compression rate when actual FPS is high (related to non-media only). 

Compression Quality During Low FPS Rate
---------------------------------------

Define the quality compression rate when actual FPS is low (related to non-media only). 

Restore System Defined Values
-----------------------------

Select this option to restore all display settings to their system-defined default values
