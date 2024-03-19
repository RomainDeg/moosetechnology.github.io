---
layout: page
background: '/img/bg-wiki.jpg'
title: VerveineJ
---

VerveineJ is a tool written in java that create a *json* or a  _mse_ file from Java source code.

## Installation

To install VerveineJ, you need to clone it form [VerveineJ github repositiory](https://github.com/moosetechnology/VerveineJ).
You might prefer the [latest released version](https://github.com/moosetechnology/VerveineJ/releases).

```bash
# https
git clone https://github.com/moosetechnology/VerveineJ.git

# ssh
git clone git@github.com:moosetechnology/VerveineJ.git
```

## Usage

### Quick start

To use VerveineJ, you can use [Famix Maker](https://github.com/moosetechnology/Moose-Easy) ![External documentation](https://img.shields.io/badge/-External%20Documentation-blue) or from a terminal.

From the terminal on Unix systems, you can use command line as follows:

```sh
./verveinej.sh -o MyProject.mse -autocp ../MyProjectDependenciesOrLib/ ../MyProjectSrcFolder/
```

On Windows, you should use `verveinej.bat` instead of `verveinej.sh`.

To use the JSON file format, you can specify the output format of VerveineJ:

```sh
./verveinej.sh -o MyProject.json -format json -autocp ../MyProjectDependenciesOrLib/ ../MyProjectSrcFolder/
```

### Options

In the following, we describe the options of VerveineJ.

Usage:

`VerveineJ [-h] [-i] [-format (mse|json)] [-prettyPrint] [-o <output-file-name>] [-summary] [-alllocals] [-anchor (none|default|assoc)] [-cp CLASSPATH | -autocp DIR] [-1.1 | -1 | -1.2 | -2 | ... | -1.7 | -7] <files-to-parse> | <dirs-to-parse>"`

| VerveineJ options | description |
| :---: | :--- |
| `-h`                                      | prints this message |
| `-i`                                      | toggles incremental parsing on (can parse a project in parts that are added to the output file) |
| `-format (mse|json)`                      | specifies the output format (default: MSE) |
| `-prettyPrint`                            | toggles the usage of the json pretty printer |
| `-o <output-file-name>`                   | specifies the name of the output file (default: ouput.mse) |
| `-summary`                                | toggles summarization of information at the level of classes. Summarizing at the level of classes does not produce Methods, Attributes, Accesses, and Invocations. Everything is represented as references between classes: e.g. \"A.m1() invokes B.m2()\" is uplifted to \"A references B\". |
| `-alllocals`                              | Forces outputing all local variables, even those with primitive type (incompatible with \"-summary\") |
| `-anchor (none|entity|default|assoc)` | options for source anchor information: - no entity - only named entities \[default\] - named entities+associations (_i.e._ accesses, invocations, references) |
| `-cp CLASSPATH`                           | classpath where to look for stubs |
| `-autocp DIR`                             | gather all jars in DIR and put them in the classpath |
| `-filecp FILE`                            | gather all jars listed in FILE (absolute paths) and put them in the classpath |
| `-excludepath GLOBBINGEXPR`               | A globbing expression of file path to exclude from parsing |
| `-1.1 | -1 | -1.2 | -2 | ... | -1.7 | -7` | specifies version of Java |
| `<files-to-parse>|<dirs-to-parse>`        | list of source files to parse or directories to search for source files |
{: .table }

### Advanced Options

#### Dealing with accent in code

It is possible to parse code with accent using a Java vm option.

To do so, add the encoding before a double dash `--`. For example:

```sh
./verveineJ.sh -Dfile.encoding=ISO-8859-1 -- -format json <...>
```

## Using docker

It is also possible to use VerveineJ with [Docker](https://github.com/Evref-BL/VerveineJ-Docker).
Please look at the repository documentation.
