.. _backup-restore:

Backup and Restore
=======================================

As :term:`RCC` is built upon AWS we're making use of the automated backup systems they provide.
As such you are able to make use of these features in the event of data loss/corruption to restore from an alternate point in time.

.. _restoring_machines:

Restoring Machines
---------------------------------------

Due to the technical implementation automated backups show up under the packages section in Ronin, but it is not where they are restored from.


.. image:: images/project_packages.png
    :class: float-right
    :scale: 50%

As our backups are essentially packages, a restore is performed by `creating a new machine <https://blog.ronin.cloud/create-a-machine/>`_ and searching the "Project Packages" section under Step 1 of the machine creation screen.

Here you may find that there is a mix of your own self created :term:`project packages<Package>` and the scheduled backups. If you have a lot of machines it can become a little difficult to see the wood for the trees.

.. rst-class:: float-right

It's usually best to use the search function at the top right to find the name of the machine you are looking to restore. This can even be a machine you may have deleted within the retention period.

.. image:: images/packages_restore.png
    :class: float-right
    :scale: 35%

Once you have found your target machine in the list, select one that has a date of creation you're happy with (you may wish to go further back in time), close the packages window and continue as if you were going to create a new machine.

What you have essentially done here is clone a macihne from a set point in time. You may even still have the source machine running while this is happening.

After all is said and done you should now have a freshly restored machine.

.. rst-class:: float-right

.. warning:: 
    As your restored machine is being spun up background tasks will kick in to make sure that it is up-to date. This ensures machines that have been restored from months old backups have the latest updates applied immediately.
    
    You may find that the machine reboots itself one or more times without warning shortly after creation.

.. note:: 
    If your restored machine is running the Windows family of OSes you'll find that the computer name gets '-restored' suffixed to avoid naming conflcts.
