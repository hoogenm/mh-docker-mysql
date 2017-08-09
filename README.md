
With the original mysql docker image (5.7), I could not use a (CIFS-) mounted volume for `/var/lib/mysql` because the
image tried to do an ssl_rsa setup which requires setting Unix access (filesystem) permissions.

A solution is to remove the `/usr/bin/mysql_ssl_rsa_setup` executable from the image. If this file is not present, the mysql image
will skip the step that is incompatible with a folder `/var/lib/mysql` that does not support Unix file permissions.
