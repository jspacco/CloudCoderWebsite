---
layout: default
title: How to update CloudCoder
---
[Prev](commands.html) | Next

### Updating CloudCoder

We may distribute new pre-compiled CloudCoder binaries (bug fixes, new features, etc).  To take advantage of these new binaries:

1. Shutdown your current CloudCoder builders ([instructions here](builder.html))

2. Shutdown your current CloudCoder server ([instructions here](commands.html))

3. Copy your current cloudcoderApp.jar and cloudcoderBuilder.jar files to a separate folder (i.e. don't copy over your existing cloudcoderApp.jar and cloudcoderBuilder.jar files) in case the new binaries don't work.

4. [Download](../downloads/downloads.html) the new binaries into the `cloudcoder` folder.

5. Configure the new binaries

		java -jar cloudcoderApp.jar configure

6. Upgrade the database

	Run this command from the `cloudcoder` folder:

		java -jar cloudcoderApp.jar migratedb

7. Copy cloudcoderApp.jar to `cloudcoder/webapp` and cloudcoderBuilder.jar `cloudcoder/builder`

	You can skip this step if you previously created symlinks.

8. Start the server ([instructions here](deploy.html))

9. Start the builder ([instructions here](builder.html))

