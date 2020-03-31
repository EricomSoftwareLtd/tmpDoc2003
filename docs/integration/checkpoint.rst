*******************
Check Point Gateway 
*******************

Check Point Gateway can integrate with Ericom Shield in the Proxy Chain scenario.
Check Point sits at the perimeter of the network and acts as the first line of defense between Ericom Shield and the Internet.
For the safest and most secure deployment, Ericom strongly recommends placing the Ericom Shield layer in the DMZ.
The hereunder refers to Check Point R80.10.

Architecture
============

.. figure:: images/checkPointChain.png	
	:scale: 75%
	:align: center

Data Flow
=========

*   End-user requests a website and uses Ericom Shield as a web proxy

*   Ericom Shield attempts to navigate to the requested URL and passes the request to Check Point

*	If the Check Point policy (e.g. whitelist) allows the request, the web content will be retrieved

*	The retrieved web content is first inspected by Check Point

*	The inspected web content is then passed to Ericom Shield for viewing

*	Ericom Shield opens the content in disposable Linux containers and sends a safe visual stream of pixels to the end-user’s browser

*	Once the user ends the browsing session by closing the browser tab, or the browser, the Linux container is destroyed

Ericom Shield Configuration
===========================

Ericom Shield supports the configuration of an upstream proxy, port number and trusted certificate. Ericom has certified that Check Point may be 
configured in this manner - where all browsing traffic originating from Ericom Shield will be filtered and protected by Check Point. To configure 
Check Point in Ericom Shield follow these steps:

*	Go to Administration Console | Settings | Proxy & Integration section

*	Enable the ``Use External Upstream Proxy`` and fill in the required settings in the ``External Upstream Proxy Configuration`` subsection.

*	If white URLs are required to pass throught Shield proxy, enable the ``Use Internal Upstream Proxy`` and fill in the required settings
in the ``Internal Upstream Proxy Configuration`` subsection.

*	Upload the Client Certificate (public & private keys)

Testing of Interconnectivity
============================

Prior to using Shield with Check Point, web pages are loaded **into** the local browser.
Any malicious content in the website would reach the actual device and could cause permanent damage.
This is the source contents of a web page reaching the local browser

.. figure:: images/viewsourcenoshield.png	
	:scale: 75%
	:align: center

Once the end-user is using Ericom Shield and Check Point, all web page content is rendered and executed in the Ericom Shield 
isolation layer and never reaches the end-point device. Below is the source contents of a web page isolated by Ericom Shield as it is 
rendered on the local browser. Native web content is completely opened and executed in a remote Ericom Shield browsing container and 
destroyed once the browser session ends. Only a safe visual pixel stream reaches the end-point device.

.. figure:: images/viewsourceshield.png	
	:scale: 75%
	:align: center

To confirm that the inbound web content is using Check Point as the first line of defense, the user simply has to visit a website 
that can detect the perimeter address, such as www.whatismyip.com to verify that the inbound address matches that of the Check Point.