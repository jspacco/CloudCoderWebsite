---
layout: default
title: Deploy the CloudCoder webapp (the server)
---
[Prev](configure.html) | [Next](builder.html)

### Prepare the webapp and builder directories

You should have the following structure:

	cloudcouder/
	cloudcoderApp.jar
	cloudcoderBuilder.jar
	cloudcoder.properties
	webapp/
	builder1/

On Linux or Mac OS X, you can create symlinks to cloudcoderApp.jar and cloudcoderBuilder.jar in the webapp and builder directories, like this:

	cd /path/to/cloudcoder/webapp
	ln -s ../cloudcoderApp.jar
	cd ../builder1
	ln -s ../cloudcoderBuilder.jar

Or you can just copy cloudcoderApp.jar into `webapp` and cloudcoderBuilder.jar into `builder1`.

### Starting the server

To start the server, run this command from inside the `webapp` folder:

	java -jar cloudcoderApp.jar start

This will create two files (instance-xxxx.fifo\| and instance.pid) and a log directory.

![Tip](../img/ktip.png) For those who are curious:  instance.pid will contain a number that is the pid (Process
Identifier) of the CloudCoder webapp process, while instance-xxxx.fifo\|
(xxxx will be replaced by the pid number) is a FIFO pipe that is used
to shutdown the process.  You should **never** delete these files
manually, and you should not need to worry about them, except to note
that their existence indicates that cloudcoder should be running.

### Shutting down the server

To shutdown the, server, run this command from the `builder1` folder:

	java -jar cloudcoderApp.jar shutdown

A normal shutdown will delete the instance-xxxx.fifo\| and the
instance.pid files.

If CloudCoder doesn't exit after two or three minutes, you can kill
the process using the pid found in instance.pid.  

### Check that the CloudCoder webapp works

Navigate to [http://localhost:8081](http://localhost:8081) (be sure to replace 8081 with the value of _cloudcoder.webserver.port_ from your cloudcoder.properties file).

Log in with the username and password you set in the previous step while creating the database.

You should be able to see the Demo Course, with one exercise in the C language.





