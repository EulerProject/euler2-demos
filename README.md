# euler2-demos2

Demos that exercise features for the euler2 toolkit.

* `./run` Use this script to replays a scenario
* `./run_all` Automatically exercises all scenarios contained
* `./demos/{demo}` A demo consists of a list of labeled euler2 commands in a yaml format.
* `./datastes/{dataset}` A dataset available for input to euler2
* `./output/{demo}/{dataset}/{any}` Any output produced by the demo for a dataset

commands example:

```
version:
 euler2 --version
help:
 euler2 --help
```
 
run examples:

* `./run all`: executes all commands of the demo in consecutive order
* `./run help`: executes the command labeled help
* `./run version,help,...`: executes the commands given in the listed order
* `./run version-help`: executes the commands in consecutive order from label version to help
* `./run clean`: resets the demo to a state before any run execution


