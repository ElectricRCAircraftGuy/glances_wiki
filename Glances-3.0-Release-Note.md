# Breaking Changes
- Support fo **Python** 3.3 as been removed (yes Glances is still compatible with Python 2.7)
- Support for **PsUtil** < 5.3 as been removed
- **XML/RPC API** have changed between Glances 2 and Glances 3. It is **not** possible to use a Glances 2.x client with a Glances 3.x server and conversely
- **Restful API** upgraded to version 3 (default entry point: http://localhost:61208/api/3)

# New Features

### Add threads number in the process list #1259

A new stat is available for all displayed processes: thread count.

![](https://user-images.githubusercontent.com/776747/39767429-09a653e2-52e7-11e8-89c3-dff819bf14c6.png)

### A way to have only REST API available and disable WEB GUI access #1149

It is now possible to run the Restful API without the Web User Interface (UI) using the --disable-webui option.

Web UI and API (default Web server mode):

```
glances -w
Glances Web User Interface started on http://0.0.0.0:61208/
```

Web API without UI:

`glances -w --disable-webui`
`Glances Restful API Server started on http://0.0.0.0:61208/api/2/`

### Others...
- Make the left side bar width dynamic in the Curse UI #1177
-

# Bug Fixes
-
-

# Improvements
-
-

# Other Changes
-
-
