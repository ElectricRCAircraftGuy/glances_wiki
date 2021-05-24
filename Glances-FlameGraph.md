FlameGraph for Glances.

Generated with the following command lines:

```
pyflame --threads -p 25527 -o ~/tmp/glances-flame.pl -s 6
flamegraph.pl ~/tmp/glances-flame.pl > ~/tmp/glances-flame.svg
```

Source:
- https://github.com/uber-archive/pyflame
- https://github.com/brendangregg/FlameGraph

