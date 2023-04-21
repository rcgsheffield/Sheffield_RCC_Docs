.. _updates:

Updates
-------

Although in :term:`RCC` we try to take a hands off approach where possible,
providing administrative level access to the systems you deploy,
we as service providers have to ensure systems are kept up to date with the latest security patches.

To do this some level of intrusive behavior is inevitable given certain updates will require a restart of the underlying operating system. 

Sadly we cannot disable this behavior without compromising security,
furthermore attempts to suspend built in operating system update mechanisms may lead to termination of your instance.

There are 2 systems in place that keep your systems updated, an automatic schedule and a task run at startup of your :term:`instances<Instance>`.

.. _schedule:

Schedule
========

The scheduled updates run every **Tuesday at 23:00** and are considered to be intrusive.
This means that if the updates applied on this schedule require it, the host machine will reboot without warning.

This is a requirement to ensure long lived instances aren't getting updates installed but not fully applied due to ignored reboot alerts.

We recommend that where possible you design your workloads to expect this form of infrequent interruption, continuing from where it left off.

.. _onstartup:

On Startup
==========

As you are in control over your machines, particularly when they are and aren't running,
there could be times where a machine is sat offline for an extended period of time. 
If this happens it could be in need of more than one critical update.

For this reason, at the startup of any instance an intrusive update is run. 
Similar to the schedule this will install any missing updates and reboot if necessary.

.. note::

    This can lead to some confusion when connecting to instances shortly after starting them. They might catch an update and suddenly reboot.
    Fear not, this is expected behavior on machines that have been off for a while.
