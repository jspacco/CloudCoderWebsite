---
layout: default
title: Complete list of CloudCoder command-line options to manage your installation
---
[Prev](builder.html) | [Next](update.html)

### Configure new cloudcoder properties

There are two situations where this would be useful:

1.  You want to change the settings of an existing CloudCoder
installation
2.  You want to apply existing configuration properties to a new
binary distribution (we may distribute new binaries with bug fixes, new features, etc)

In either case, you should shutdown your cloudcoder installation
before re-configuring a binary jarfile.

	java -jar cloudcoderApp.jar configure

Here is a [sample transcript of configuring the webapp and the builder](configure-transcript.txt).

![Tip](../img/ktip.png) cloudcoderApp.jar configures both the webapp and
 the builder.

### Update the database tables

First, shutdown cloudcooder.  Then run this command from the `webapp` folder:

	java -jar cloudcoderApp.jar migratedb

This will bring update your cloudcoder tables, adding new columns or
new tables where necessary.

### List configuration properties

From the directory containing `cloudcoderApp.jar`, run this command:

	java -jar cloudcoderApp.jar listconfig

### Register students

In the folder containing `cloudcoderApp.jar`, register students by running this command:

	java -jar cloudcoderApp.jar registerstudents

This command will prompt for the name of a tab-delimited text file.  This file should have a number of tab-delimited lines in the following format:

`username	firstname	lastname	email	password	section`

The section is optional (it will default to 101 if you leave it out)

Students can change their passwords once they log into the system.
Instructors can also change student passwords.

### Create a new user account (student or instructor)

	java -jar cloudcoderApp.jar createuser

Then follow the prompts to set up the new account's name, email, username and password.

### Start the server

From the `webapp` folder (either containing `cloudcoderApp.jar` or
containing a symlink to `cloudcoderApp.jar`):

	java -jar cloudcoderApp.jar start

### Shutdown the server

From the `webapp` folder (either containing `cloudcoderApp.jar` or
containing a symlink to `cloudcoderApp.jar`):

	java -jar cloudcoderApp.jar shutdown

### Create the cloudcoder database (Should only be done once!)

In the folder containing `cloudcoderApp.jar`:

	java -jar cloudcoderApp.jar createdb

Here is a [sample transcript of creating the database](createdb-transcript.txt).

### Start the builder (from the builder directory)

	java -jar cloudcoderBuilder.jar start

### Stop the builder (from the builder directory)

	java -jar cloudcoderBuilder.jar shutdown
