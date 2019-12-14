This page will gather all ideas concerning the future Glances 4.x branch.

The Glances philosophy is: "Monitor your computer thanks to a single view. Only for your eyes, no hands needed."

Please contribute to this roadmap. Glances is yours.

# Functional needs

* Improve the central client UI (--browser) (#1289)
* GPU monitoring for other hardware architecture (#993, #994 and #1048)
* Running both server and webserver at the same time #995 

# UI points

* Allow processlist columns to be selected in config file #1524
* Refactor Curses UI ==> https://github.com/nicolargo/pythonarena/blob/master/curses/cursesarena.py

# Technical points

* Python 3 support (Python 2 is deprecated). For Python 2 users, the branch 3.x will be maintain.
* Async IO architecture for the Core (see https://realpython.com/async-io-python/). Keep in mind to speed up Glances launch (#1534)
* Support for Windows 10 WLS (#1485)

