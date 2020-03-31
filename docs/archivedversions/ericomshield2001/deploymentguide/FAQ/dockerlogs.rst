******************************
How To Modify Docker Logs Size
******************************

Docker container logs can grow and consume a large amount of disk. It is recommended to set a limit to the logs files.

To do that, go to ``/etc/docker/`` and set the **log-driver** and **log-opts** keys. 

The following example sets the **log driver** to json-file and sets the **max-size** and **max-file** options. 
The total disk used in this case will not exceed 50MB (5*10m)::

    "log-driver": "json-file",
    "log-opts": 
    {
        "max-size": "10m",
        "max-file": "5"
    }

Modify the max-size and max-file as desired.

.. note:: When installing Shield using OVA, this can be skipped, as these values are already predefined. 

