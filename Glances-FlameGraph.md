FlameGraph for Glances.

Generated with the following command lines:

```
pyflame --threads -p 25527 -o ~/tmp/glances-flame.pl -s 60
grep -v idle ~/tmp/glances-flame.pl > ~/tmp/glances-flame-non-idle.pl
flamegraph.pl ~/tmp/glances-flame-non-idle.pl > ~/tmp/glances-flame.svg
```

[Click here to surf on the flame !](https://raw.githubusercontent.com/nicolargo/glances/develop/docs/_static/glances-flame.svg)
![Glances flame](https://raw.githubusercontent.com/nicolargo/glances/develop/docs/_static/glances-flame.svg)

Source:
- https://github.com/uber-archive/pyflame
- https://github.com/brendangregg/FlameGraph
