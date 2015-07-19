Welcome to the **Glances**, an open-source software to monitor and collect operating system statistics.

This wiki is the main point of entry for developers working with (or contributing to) the Glances project. If you are a simple user, please have a look [on the official documentation](http://glances.readthedocs.org/en/latest/).

# How to contribute ?

Glances is developed by a awesome community. If you want to join us, please open|find an opened issue scheduled in the next release. Add a simple message in the issue to inform the community that you want to contribute. If you need additional information, _do not_ use the Github issue form but directly the [Gitter chat area](https://gitter.im/nicolargo/glances?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge). 

Glances development factory uses the 'git flow' workflow. The development model is greatly inspired by existing models out there. The central repository holds two main branches with an infinite lifetime:

* master: main branch where the source code of HEAD always reflects a production-ready state. Do *NOT* pull on this branch but on the develop one.
* develop: main branch where the source code of HEAD always reflects a state with the latest delivered development changes for the next release

Please [read this page](https://github.com/nicolargo/glances/wiki/How-to-contribute-to-Glances-%3F).

# How to test ?

Glances is a multi-platform software, so we need beta-testers. If you want to install and test the develop branch, please [follow this procedure](https://github.com/nicolargo/glances/wiki/Install-and-test-Glances-DEVELOP-version). 

# Glances API

Others softwares can grab Glances statistics using the following API:

* [XMLRPC/JSON API version 2](https://github.com/nicolargo/glances/wiki/The-Glances-2.x-API-How-to) (or obsolete [version 1](https://github.com/nicolargo/glances/wiki/The-Glances-1.x-API-How-to)) 
* [RESTFUL/JSON API](https://github.com/nicolargo/glances/wiki/The-Glances-RESTFULL-JSON-API)
