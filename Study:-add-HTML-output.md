Glances HTML output

# Description

Technologies: HTML5, CSS3, templates

The HTML output is only generated if the -w tag is used.

The first time Gances starts, it creates a ~/.glances/ folder with the following files:

* base.html: the default HTML template
* default.html: the default HTML template (child of the base.html)
* default.css: the default CSS

Users can create new templates (both HTML and CSS) based on the defaults ones. To use the new templates, users had  to use the "-w templatename" option: the template.html and template.css will be loaded instead of the default one.

# Usefull libs (or not...):

* [Bottle](http://bottlepy.org/docs/dev/): create an embedded Web server (option)
* [lxml](http://lxml.de/lxmlhtml.html): a low level XML (HTML) generator
* [sphinx](http://sphinx.pocoo.org/contents.html): generate HTML used to generate thePython doc Web site
* [jinja](http://jinja.pocoo.org/docs/): generate HTML from template (some [exemples](https://github.com/mitsuhiko/jinja2/tree/master/examples))

The Jinja2 lib is good for Glances...

## Jinja

Install (Ubuntu):

`apt-get install python-jinja2`

Template exemple (base/slave): http://jinja.pocoo.org/docs/templates/

i18n plugin: http://jinja.pocoo.org/docs/extensions/