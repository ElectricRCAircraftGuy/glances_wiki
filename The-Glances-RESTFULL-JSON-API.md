**Only for Glances v2.1 or higher !**

Glances HTTP API is based on a **RESTFULL/JSON**.

Serveur side
============

    $ glances -w

    Glances Web server is running on 0.0.0.0:61208

Client side
===========

_**/api/2/pluginslist**_

Return the plugins available on the Glances server.

Request parameters: 

None

Request response:

* 200 - application/json: list
* 404 - Returned if the property does not exist


