**THIS DOCUMENT IS UNDER CONSTRUCTION**

**API COULD AND WILL CHANGE**


A deep re-factor of the Glances software architecture will be made in the version 3.0.

# Modes

First of all, it should be possible to start all the following modes individually or in parallel:
- Glances standalone or client
- Glances server
- Glances export

# Concerning API

On the previous list, you can see that i only wrote "Glances server" and not Glances XML-RPC or Restful server. Glances v3 will only implement a Restful (HTTP/JSON) API (APIv3) and breaks the compatibility with the Glances v2 API.

The APIv3 should generate JSON output message as following (example for a memory GET request):

```
{
   "metadata": {"api_version": 3,
                "plugin_name": "mem", 
                "source": "glances"}
   "stats": [{"available": 5071183872, "used": 3255848960, "cached": 1827352576, "percent": 39.1, "free": 5071183872, "inactive": 1388982272, "active": 3679604736, "total": 8327032832, "buffers": 477982720}],
   "views": [{"available": {'decoration': 'DEFAULT', 'optional': False, 'additional': False, 'splittable': False}, ...]
}
```

_Note: the 'views' field is optional (the GET request should allow to only ask for stats and metadata)_

 