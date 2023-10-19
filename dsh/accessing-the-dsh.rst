.. _accessing-the-dsh:

Accessing The DSH
=======================================

Unlike in the :term:`RCC` platform, the :term:`DSH` requires you to access the system via a `Bastion Host <https://en.wikipedia.org/wiki/Bastion_host>`_ created specifically for your project.
This comes in the form of a virtual desktop hosted in AWS WorkSpaces, for which you'll need software to access.

.. note:: 
    You will only be able to access your workspace via a University of Sheffield managed desktop while onsite (connected to the campus network).
    
    Attempting to connect while offsite, even while connected to the VPN will result in an authentication failure.

.. _install-aws-workspaces-client:

Install The AWS WorkSpaces Client
---------------------------------------

Before proceeding, you'll need to ensure you have received conformation that your DSH account and workspace has been fully provisioned for use with your university account.

1. Open the Software Center, search for and ensure the "Update Computer Certificate Acl" application is available and installed:

.. image:: images/ws-install-2.png
    :align: center
    :scale: 50%

|

2. Download the latest Windows client from the `WorkSpaces <https://clients.amazonworkspaces.com/>`_ website
3. Run the WorkSpaces client installer
    - When prompted choose "Install just for you":

.. image:: images/ws-install-1.png
    :align: center
    :scale: 75%

|

4. When the installer completes open WorkSpaces and enter your workspace registration code

.. image:: images/ws-install-3.png
    :align: center
    :scale: 75%

You should now be ready to enter your login credentials.

Understanding Your Access
---------------------------------------

Now that you have a way into the DSH, you should familiarize yourself with the different things you can and cannot access via your workspace.

.. image:: images/project-architecture.jpg
    :align: center

|

The diagram above shows a simplified layout of your access in the DSH.
From your workspace you will be able to access:

* Ronin
* Machines/Instances in your project/s
* Internal Gitlab
* Internal update mirrors
* Authentication services

Machines/Instances in your projects/s will have additional access to things like:

* Object Storage
* Internal CRAN / Pypi mirrors
* Unrestricted access to each other (machines in your projects have no firewalls between each other)

Ronin
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Your workspace will come pre-configured with Firefox as the default browser.
It is configured to automatically take you to the Ronin web UI as the default home page.


Machines/Instances
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Access to your instances will be done through the Ronin Link desktop application.
Allowing you to connect to both Windows and Ubuntu machines with either SSH or remote desktop.


Object storage
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Access to object storage you create in your project is limited to the instances you assign permissions to.
You won't be able to access a bucket from your instance even with valid credentials until it is given additional permissions to do so.

External Services
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Certain projects may be granted special access outside of the DSH's firewall, this is primarily restricted to things like licensing servers.
