.. _nnbench:

NNBench - NameNode benchmark
=============================

In Hadoop clusters, the NameNode keeps the directory tree of all files in HDFS and locations of the files across the multiple DataNodes and the NNBench runs a test for the NameNode with some load. The NNBench NameNode benchmark is useful to check NameNode configuration with its hardware before running anything in production.

Sample Run of NNBench
-------------------------

.. code::

     hadoop jar /opt/hadoop/share/hadoop/mapreduce/hadoop-mapreduce-client-jobclient-2.7.1.jar nnbench -operation create_write -baseDir /user/$USER/NNBench

This command will create a file with 1 map and 1 reducer. You can change the options to increase the number of files, maps or reducers. For details, see the available options below.

Main Operations
----------------

* create_write: is an operation you should run at first. It creates a file(s) to run a test.
* open_read
* rename
* delete

Available Options
-------------------

.. code::

    Options:
    -operation <Available operations are create_write open_read rename delete. This option is mandatory>
    * NOTE: The open_read, rename and delete operations assume that the files they operate on, are already available. The create_write operation must be run before running the other operations.
    -maps <number of maps. default is 1. This is not mandatory>
    -reduces <number of reduces. default is 1. This is not mandatory>
    -startTime <time to start, given in seconds from the epoch. Make sure this is far enough into the future, so all maps (operations) will start at the same time. default is launch time + 2 mins. This is not mandatory>
    -blockSize <Block size in bytes. default is 1. This is not mandatory>
    -bytesToWrite <Bytes to write. default is 0. This is not mandatory>
    -bytesPerChecksum <Bytes per checksum for the files. default is 1. This is not mandatory>
    -numberOfFiles <number of files to create. default is 1. This is not mandatory>
    -replicationFactorPerFile <Replication factor for the files. default is 1. This is not mandatory>
    -baseDir <base DFS path. default is /becnhmarks/NNBench. This is not mandatory>
    -readFileAfterOpen <true or false. if true, it reads the file and reports the average time to read. This is valid with the open_read operation. default is false. This is not mandatory>
    -help: Display the help statement

