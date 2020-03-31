*****************************************************************
How To Configure A System With Multiple Authentication Components
*****************************************************************

In systems which include more than one method for authenticating users, e.g. 

*   A preliminary component such as proxy or secure gateway (out of Shield system)

*   Internal Active Directory (within Shield System)

It is possible to define and use both the **Authentication Chaining** and the **LDAP** authentication methods.


An example for the authentication flow in this scenario:

*   User connects to external component out of Shield (e.g. squid proxy)

*   User is authenticated (or not), according to proxy rules

*   Proxy creates the X-Authenticated-User header with the authenticated username (if exists) 

*   Shield uses the username from the header for the profile based rules. If the username is empty/missing - the profile used will be "All".

.. note:: In this scenario, Shield will not preform any actual authentication, and rely solely on the X-Authenticated-User header for user authentication.