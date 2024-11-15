.. _data-ingress:

Data Ingress
============

This document is focused on external data ingress methods supported by the :term:`RCC` platform.
If you are an internal user looking to upload data to the platform you may wish to look at other available methods available to you such as: :ref:`object-storage`

.. _sftp:

SFTP
----

.. note::
    The SFTP service is made available to approved data providers upon request, if you've not been explicitly pointed towards using this service then you most likely don't have access.
    Access is provided on a project by project basis depending on data sharing agreements.

    If this service looks like a good fit for your needs please get in touch with us via the IT Services Helpdesk or if you are an external data provider please reach out to your UoS contacts.

Generating Keys
^^^^^^^^^^^^^^^

Should you be granted access to the service you'll need to generate an RSA or ECDSA key pair, and forward the public key to your internal contact.

.. tabs::

    .. group-tab:: Windows

        We suggest you use PuTTYgen to generate keys on Windows machines. This is included in the full installer of Putty found `here. <https://www.putty.org/>`_
        
        From PuTTYgen select either ``EdDSA`` or ``RSA`` as the type of key to generate, then click on "Generate":

        .. image:: images/sftp/putty-gen.png
            :align: center
            :scale: 50%
        
        |

        With the key generated we **highly** recommend you enter a strong password in the key passphrase fields before saving the private key.
        As the name suggests this key is private and should not be shared with anyone!

        You'll also want to save the public key, this is the file you'll need to send on to your internal contact.

    .. group-tab:: Mac/Linux

        Mac and Linux machines come with the ``ssh-keygen`` command baked in and can be used here to generate the keys we require.

        Run the below via a terminal replacing ``<key-name>`` with a filename of your choosing. You may wish to ``cd`` into a suitable directory first.

        .. code-block::

            ssh-keygen -t ed25519 -f <key-name>

        This command will ask you to enter a passphrase for the key, we **highly** recommend you do so.

        Once this has been entered the system will generate 2 new files, your private key is the file with the name you specified after the ``-f`` and the public key which is the same again but suffixed with ``.pub``

        Take care to keep your private key safe as it should not be shared with anyone!
        The ``<key-name>.pub`` file should be forwarded onto your internal contact.

Connecting
^^^^^^^^^^

Once you've been given the green light that your account has been created with the public key you've provided from the steps above
you'll want to connect into the service to start transferring data.

``sftp.rcc.shef.ac.uk`` via port ``22`` is the primary endpoint for accessing the service.
Use this when configuring the server address and port with the software suggested below.

.. tabs::

    .. group-tab:: Windows

        Although we're tool agnostic this document providing step by step guidance for `WinSCP <https://winscp.net/eng/index.php>`_.
        Should you feel confident with configuration other good tools such as `FileZilla <https://filezilla-project.org/>`_ will work just fine.

        You'll first need to change some settings in WinSCP:

        Open the preferences dialogue box from the Options menu in the top right.

        .. image:: images/sftp/winscp-options.png
            :align: center
            :scale: 75%
        
        |
        
        From here navigate to the "Transfer" tab, select "Default" and "Edit...":

        .. image:: images/sftp/winscp-preferences.png
            :align: center
            :scale: 75%
        
        |
        
        This will open the "Transfer settings" box, from here ensure the "Preserve timestamp" box is **unchecked**:

        .. image:: images/sftp/winscp-transfer-settings.png
            :align: center
            :scale: 75%
        
        |
        
        After confirming the transfer settings, enter the "Endurance" tab below and set the "Enable transfer resume/transfer to temporary filename for" setting to "Disable":

        .. image:: images/sftp/winscp-endurance-settings.png
            :align: center
            :scale: 75%
        
        |

        With these now set you may need re-open WinSCP to see the ``Login`` form, once open you'll want to make sure that the file protocol ``SFTP`` is selected:

        .. image:: images/sftp/winscp-login.png
            :align: center
            :scale: 50%
        
        |

        With the server address entered in the host name and user name fields entered in you'll want to click on the ``Advanced...`` button to select your private key.

        .. image:: images/sftp/winscp-advanced.png
            :align: center
            :scale: 50%
        
        |

        From the left hand side of this new menu go to the ``SSH - Authentication`` tab and under the text box for ``Private key file:`` click on the ``...`` button to open a file selection prompt.
        This will allow you to select the private key ``.ppk`` file you generated in the steps above.

        With those filled you should now be able to log into the SFTP service.

    .. group-tab:: Mac/Linux

        We don't yet have specific guidance on connecting to the SFTP service via Mac or Linux machines,
        however there are many good tools out there that we're happy to suggest:

        * `Cyberduck <https://cyberduck.io/>`_ for Mac
        * `FileZilla <https://filezilla-project.org/>`_ for Linux or Mac
