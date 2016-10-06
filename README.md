# euler2-demos2

Demos that exercise features for the euler2 toolkit.

* `./run` Use this script to replay a scenario
* `./run_all` Automatically exercises all demos contained
* `./commands/{commands}` A demo consists of a list of labeled euler2 commands in a yaml format.
* `./examples/{example}` A dataset available for input to euler2
* `./output/{commands}/{example}/{any}` Any output produced by the commands using the given example as input

commands example:

```
input_viusalization:
 euler2 show taxonomies.txt articulations.txt iv
align:
 euler2 align taxonomies.txt articulations.txt
show_possible_worlds:
 euler2 show pw
```
 
run examples:

* `./run all`: executes everything of the commands in consecutive order
* `./run help`: executes the command labeled help
* `./run align,input_visualization,...`: executes the commands given in the listed order
* `./run align-show_possible_worlds`: executes the commands in consecutive order from label align to show_possible_worlds
* `./run clean`: resets the commands output to a state before any run execution


