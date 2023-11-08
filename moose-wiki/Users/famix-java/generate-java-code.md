---
layout: page
author: Benoit Verhaeghe
background: '/img/bg-wiki.jpg'
title: 'Generate Java Code'
---

One common action one want to perform is to generate the Java code that corresponds to a model.
It is often the last part of performing [Model Driven Engineering](https://en.wikipedia.org/wiki/Model-driven_engineering).
It is also named, the *Forward Engineering*.

The Moose platform includes a tool to perform such an action, it is named [FAMIX2Java](https://github.com/moosetechnology/FAMIX2Java).
In this page, you will learn how to install the tool and generate Java code based on a [Famix Java model pre-loaded from a file](../ImportingAndExportingModels), and generated with [VerveineJ](../../Developers/Parsers/VerveineJ).

## Installation

To install FAMIX2Java, first, start your Moose image.
Then, in a playground (*Browse>Playground*) perform the following script:

```st
Metacello new
  githubUser: 'moosetechnology' project: 'FAMIX2Java' commitish: 'v4' path: 'src';
  baseline: 'Famix2Java';
  load
```

This will install the package `Famix2Java` in which we will find the code of the exporter.

## Export the code

Once you have loaded the project, it is possible to regenerate the Java project based on the model.
To do so, you only have to execute

```st
FAMIX2JavaVisitor new
    rootFolder: 'D:\exported' asFileReference;
    export: model.
```

**Note** that since FamixJava is a high-level meta-model (*not representing the code inside a method*), it will not be able to regenerate the code inside the method, but only the structural part.
However, if you have set a root folder (see [Import model](../ImportingAndExportingModels)), and not modified that much the model, the exporter will retrieve the code of the method to export based on the sources.
If you need to modify the code of methods, see you next section :smile:

## Export method code

You might want to modify the code inside method and export it.
This is not part of the FamixJava exporter project, however, the Moose platform include two others project that can help you.

First, you should check [FAST-Java](../../Developers/Parsers/FAST-Java) that allows one to represent the code of a method, modify it, and regenerate it.
Second, if you want to use both FAST-Java, and Famix, you can have a look at [Carrefour]({% post_url 2022-06-30-carrefour %}) which brings together the two world.