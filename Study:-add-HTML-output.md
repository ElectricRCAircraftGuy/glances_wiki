Usefull libs (or not...):

* [Bottle](http://bottlepy.org/docs/dev/): create an embedded Web server
* [lxml](http://lxml.de/lxmlhtml.html): a low level XML (HTML) generator
* [jinja](http://jinja.pocoo.org/docs/): generate HTML from template (some [exemples](https://github.com/mitsuhiko/jinja2/tree/master/examples))

# Jinja

Install (Ubuntu):

`apt-get install python-jinja2`

Sandbox:

`
$ python
>>> import jinja2
>>> env = jinja2.Environment(line_statement_prefix="#", variable_start_string="${", variable_end_string="}")
>>> print env.from_string("""\
... <ul>
... # for item in range(10)
...     <li class="${loop.cycle('odd', 'even')}">${item}</li>
... # endfor
... </ul>\
... """).render()
<ul>
    <li class="odd">0</li>
    <li class="even">1</li>
    <li class="odd">2</li>
    <li class="even">3</li>
    <li class="odd">4</li>
    <li class="even">5</li>
    <li class="odd">6</li>
    <li class="even">7</li>
    <li class="odd">8</li>
    <li class="even">9</li>
</ul>
`



