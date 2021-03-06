<img src="http://euler.cs.ucdavis.edu/_/rsrc/1366832610901/home/logo_small.png" alt="The EulerX toolkit" width="100" height="88">
#euler2-demos
This repository is for demos of the [EulerX](https://github.com/EulerProject/EulerX) toolkit.

### Introduction
Here we demonstrate how the [EulerX](https://github.com/EulerProject/EulerX) toolkit 
developed by the EulerProject team allows to solve the taxonomy alignment problem 
[<a href="http://www.slideshare.net/taxonbytes/ludaescher-etal-2014hybriddiagnosisconceptreasoning" target="_blank">1</a>, <a href="http://taxonbytes.org/pdf/ChenEtAl2014-HybridDiagnosisApproach.pdf" target="_blank">2</a>].
A python script exercises commmands that make up demos on example taxonomy alignment problems.
Additionally, this repository stores the correct outputs of the demos for the purpose of testing EulerX development efforts.

### How to use
#### 1. Replay a demo and inspect executed commands
<a target="_blank" href="http://content.screencast.com/users/thomas.rodenhausen/folders/Jing/media/fb65bc4b-0dcf-4fce-b41c-1d4214c2aa4a/2016-10-19_1418.swf&blurover=false"><img src="https://img.youtube.com/vi/BbqY7htrY5U/0.jpg" alt="Replay a demo and inspect executed commands" 
width="180" height="120"></a>

#### 2. Replay a demo and compare its output to the repository HEAD
<a target="_blank" href="http://content.screencast.com/users/thomas.rodenhausen/folders/Jing/media/213791ed-4dda-46b2-8304-442f37d845d8/2016-10-20_1036.swf&blurover=false"><img src="https://img.youtube.com/vi/BbqY7htrY5U/0.jpg" alt="Replay a demo and compare its output to the repository HEAD" 
width="180" height="120"></a>

#### 3. Replay two demos (vary reasoner on the same taxonomy alignment problem) and compare their outputs
<a target="_blank" href="http://content.screencast.com/users/thomas.rodenhausen/folders/Jing/media/7144d074-0eb8-452c-99f5-9a1bc4cdcc76/2016-10-20_1051.swf&blurover=false"><img src="https://img.youtube.com/vi/BbqY7htrY5U/0.jpg" alt="Replay two demos (vary reasoner on the same taxonomy alignment problem) and compare their outputs" 
width="180" height="120"></a>

### Prerequisites
Python 2.7.x, [EulerX](https://github.com/EulerProject/EulerX) 

### Repository organization

Overall sturcture of the repository: 

Directory                              | Description
-----------------------------------------------------------------|------------
./commands/{commands}                   						 | Commands files containing a list of labeled EulerX commands and their documentation yaml format.
./examples/{example}/taxonomies.txt    							 | Input taxonomies and corresponding articulations sets
./examples/{example}/{articulations}/articulations.txt			 | Input articulations for an example
./output/{commands}/{example}/{articulations}/{reasoner}/*	     | Output produced by commands using given example input taxonomies, articulations and reasoner as applicable
./EULER_WORKFLOW.md												 | Documentation of the internal workflows of EulerX
./README.md														 | The documentation of this repository
./compare														 | Python script to compare the output between demos locally, or with the stored output of the same demo in the repository HEAD.
./compare_reasoner          | Python script to compare the reasoner output between demos locally
./run															 | Python script to replay a demo
./run_all														 | Python script to replay a set of demos

#### ./commands/{commands} example:

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
 
#### ./examples/{example}/taxonomies.txt example:

```
taxonomy 1997 D’Abrera
(Amauris_damocles)
(Amauris_hyalites Amauris_hyalites_subsp_hyalites Amauris_hyalites_subsp_makuyensis)

taxonomy 1995 AckeryEtAl
(Amauris_damocles Amauris_damocles_subsp_damocles Amauris_damocles_subsp_hyalites Amauris_damocles_subsp_makuyensis)
```

#### ./examples/{example}/articulation.txt example:

```
articulation 1997-1995 D’Abrera-AckeryEtAl
[1997.Amauris_damocles equals 1995.Amauris_damocles_subsp_damocles]
[1997.Amauris_hyalites_subsp_hyalites is_included_in 1995.Amauris_damocles_subsp_hyalites]
[1997.Amauris_hyalites_subsp_makuyensis equals 1995.Amauris_damocles_subsp_makuyensis]
```

### Script usage
#### ./run usage:

```
Runs a demo contained in this repository
Usage: run [OPTIONS]

Options:
  --commands TEXT       Choose one of the available commands files
                        (./commands/{commands})
  --example TEXT        Choose one of the available examples
                        (./examples/{example})
  --articulations TEXT  Choose one of the available example articulations
                        (./examples/{example}/{articulations}
  --target TEXT         Choose between 'all', a list ('command1,command2,...')
                        or a sequence ('command1-command3') of command labels
                        or 'clean'. You can find the command labels in the
                        selected commands file. Default: all
  --reasoner TEXT       Choose between 'dlv' and 'gringo'
  --help                Show this message and exit.

```

#### ./run_all usage:
```
Runs all demos contained in this repository, meeting the options provided.
E.g. 
run_all --commands=align,pipeline --examples=oaks
executes
run --commands=align --example=oaks --articulations=alice_articulations --reasoner=dlv
...
run --commands=align --example=oaks --articulations=gaby_articulations --reasoner==dlv
run --commands=align --example=oaks --articulations=alice_articulations --reasoner=gringo
...
run --commands=align --example=oaks --articulations=gaby_articulations --reasoner=gringo
run --commands=pipeline --example=oaks --articulations=alice_articulations --reasoner=dlv
...
run --commands=pipeline --example=oaks --articulations=gaby_articulations --reasoner=dlv
run --commands=pipeline --example=oaks --articulations=alice_articulations --reasoner=gringo
...
run --commands=pipeline --example=oaks --articulations=gaby_articulations --reasoner=gringo

Usage: run_all [OPTIONS]

Options:
  --commands TEXT       Provide a comma separated list from the available
                        commands files (./commands/{commands})
  --examples TEXT       Provide a comma separated list from the available
                        examples (./examples/{example})
  --articulations TEXT  Provide a comma separated list from the available
                        example articulations
                        (./examples/{example}/{articulations}
  --target TEXT         Choose between 'all', a list ('command1,command2,...')
                        or a sequence ('command1-command3') of command labels
                        or 'clean'. Default: all
  --reasoners TEXT      Provide a comma separated list from the available
                        reasoners:  'dlv' and 'gringo'
  --help                Show this message and exit.

```

#### ./compare usage:

```
Compares the output between demos locally, or with the stored output of the same demo in the repository HEAD.
Usage: compare [OPTIONS]

Options:
  --commands TEXT          Provide a comma separated list from the available
                           commands files (./commands/{commands})
  --examples TEXT          Provide a comma separated list from the available
                           examples (./examples/{example})
  --articulations TEXT     Provide a comma separated list from the available
                           example articulations
                           (./examples/{example}/{articulations}
  --reasoners TEXT         Provide a comma separated list from the available
                           reasoners:  'dlv' and 'gringo'
  --compare_gold_standard  Compare output of demo to corresponding output at
                           repository HEAD
  --help                   Show this message and exit.

```

#### ./compare_reasoner usage:

```
Compares the reasoneroutput between demos locally
Usage: compare_reasoner [OPTIONS]

Options:
  --commands TEXT       Choose one of the available commands files
                        (./commands/{commands})
  --example TEXT        Choose one of the available examples
                        (./examples/{example})
  --articulations TEXT  Choose one of the available example articulations
                        (./examples/{example}/{articulations}
  --help                Show this message and exit.
```
