.. _drive-storage:

Drive Storage
=======================================

Drive storage, or 'block storage' as it's sometimes more generally referred to as, is the storage attached directly to your :term:`instances<instance>` within Ronin.  
The other main type of stored available in Ronin is :ref:`object-storage`.  Drive/block storage offers better performance for both reading/writing data and also for file metadata queries, but object storage is cheaper and offers larger capacities.   

These are most commonly the 'Root Drive' however Ronin gives you the option to create your own additional drive/block storage devices that can be attached to instances and moved _between_ instances.

Should you want to know about the nitty gritty, the underlying technology used here is `AWS EBS <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html>`_.

.. _drive_types:

Drive Types
---------------------------------------

When creating a new non-root drive, Ronin gives you multiple options for drive types.
As a general rule of thumb we recommend you select **SSD**, this is due to how AWS provisions drive speed.

The SSD drives will be allocated 
* 125 MiB/s of read and write performance and 
* 3000 of IOPS ('input/output operations per second')
(as per `gp3 defaults <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/general-purpose.html#gp3-performance>`_).
Should your workload require more performance please do get in touch.

For those wondering why we omit the other drive options, this is mainly due to the behavior of the magnetic storage classes.
The HDD storage classes base their throughput off the provisioned storage size `see here <https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/hdd-vols.html>`_.
Because of this we recommend that you use :ref:`object-storage` for storing large amounts of data.
