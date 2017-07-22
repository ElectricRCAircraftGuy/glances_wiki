A deep re-factor of the Glances software architecture will be made in the version 3.0.

First of all, it will be possible to start all the following modes (/services) in parallel:
- Glances standalone or client
- Glances server
- Glances export

On the previous list, you can see that i only wrote "Glances server" and not Glances XML-RPC or Restful server. Glances v3 will only implement a Restful (HTTP/JSON) API.


 