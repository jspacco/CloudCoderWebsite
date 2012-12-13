---
layout: default
title: Download and configure the pre-compiled binaries
---
[Prev](mysql.html) | [Next](deploy.html)

## Download the binaries

Download the [pre-compiled webapp and builder binaries](../downloads/downloads.html)

Then download the template [cloudcoder.properties](cloudcoder.properties) file

This should give you 3 files (Note that binaries might have version numbers appended
to them, like cloudcoderApp-v0.1.jar):

	cloudcoderApp.jar

	cloudcoderBuilder.jar

	cloudcoder.properties

## Create your directory structure

Create a _cloudcoder_ directory, and _cloudcoder/webapp_ and _cloudcoder/builder1_ inside of it.

## Configure the CloudCoder binaries

Put all 3 files you just downloaded into the _cloudcoder_ directory
that you just created.

Enter your configuration settings into cloudcoder.properties.  Here is [much more information about the cloudcoder.properties file](cloudcoder.properties.html) to help you do so.  The main things are to make sure that you set your database configuration information correctly.

Store your configuration settings into the binaries by running this command:

	java -jar cloudcoderApp.jar configure

And follow the instructions.  This will copy the configuration properties from your cloudcoder.properties file into the two jarfiles.

Here is a [sample transcript of configuring the binaries](configure-transcript.txt).

![Tip](../img/ktip.png)  You should reply _yes_ when asked if you want to create a new keystore.  The keystore contains keys that are used for secure communication between the builder and the webapp.

![Tip](../img/ktip.png) You run the configure command using cloudcoderApp.jar, but this command configures both cloudcoderApp.jar and cloudcoderBuilder.jar.  This may not be intuitive.

### Create the cloudcoder database tables (requires a running MySQL server)

Run this command:

	java -jar cloudcoderApp.jar createdb

Here is a [sample transcript of creating the database](createdb-transcript.txt).

This command creates the cloudcoder database tables, as well as your initial cloudcoder user account.  Note that the database should not already exist, but the mysql account should have sufficient permissions to create it.  You will be prompted for the cloudcoder username and password you would like to use; you will use this username/password to log into the cloudcoder server and it does not need to match the mysql username or any other username.  

![Tip](../img/ktip.png) Be sure to use the default value for the exercise repository (`https://cloudcoder.org/repo`) or you will not be able to download or upload shared exercises.  This value is stored in the database, not in the cloudcoder.properties file.

### List your configuration properties

List your configuration properties, and ensure they match the values in your cloudcoder.properties files.

	java -jar cloudcoderApp.jar listconfig


