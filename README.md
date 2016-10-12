# euler2-demos2

Demos that exercise features for the euler2 toolkit.

* `./run` Use this script to replay a demo
* `./run_all` Automatically exercises a set of demos contained
* `./commands/{commands}` A commands file consists of a list of labeled euler2 commands in a yaml format.
* `./examples/{example}` Example data available for input to euler2
* `./output/{commands}/{example}/{articulations}/{reasoner}/{any}` Any output produced by the commands using the given example as input and optionally the articulations and reasoner

commands example:

```
input_viusalization:
 command: euler2 show iv taxonomies.txt articulations.txt
 doc: https://github.com/EulerProject/EulerX/wiki/Euler-Reasoning-Tool#consistent-example-abstract4
align:
 command: euler2 align taxonomies.txt articulations.txt
 doc: https://github.com/EulerProject/EulerX/wiki/Euler-Reasoning-Tool#general-commands
show_possible_worlds:
 command: euler2 show pw
 doc: https://github.com/EulerProject/EulerX#5-show-the-possible-worlds
```
 
example example:

```
taxonomy 1997 D’Abrera
(Amauris_damocles)
(Amauris_hyalites Amauris_hyalites_subsp_hyalites Amauris_hyalites_subsp_makuyensis)

taxonomy 1995 AckeryEtAl
(Amauris_damocles Amauris_damocles_subsp_damocles Amauris_damocles_subsp_hyalites Amauris_damocles_subsp_makuyensis)
```
 
run usage:

```
Usage: run [OPTIONS]

Options:
  --commands TEXT       Choose from one of the available commands files
  --example TEXT        Choose from one of the available examples
  --articulations TEXT  Choose from one of the available example articulations
  --target TEXT         Choose between 'all', a list ('align,input_visualization,...')
                        or a sequence ('align-show_possible_worlds') of command labels
                        or 'clean'. Default: all
  --reasoner TEXT       Choose between 'dlv' and 'gringo'
  --help                Show this message and exit.
```

run_all usage:
```
Usage: run_all [OPTIONS]

Options:
  --commands TEXT       Choose from one of the available commands files
  --examples TEXT       Choose from one of the available examples
  --articulations TEXT  Choose from one of the available example articulations
  --target TEXT         Choose between 'all', a list ('align,input_visualization,...')
                        or a sequence ('align-show_possible_worlds') of command labels
                        or 'clean'. Default: all
  --reasoners TEXT      Choose between 'dlv' and 'gringo'
  --help                Show this message and exit.
```

