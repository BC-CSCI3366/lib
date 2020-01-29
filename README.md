# CSCI 1103 and CSCI 3366 OCaml Support

This repository has two resources that support the execution of OCaml code in a REPL. The first resource is needed only by students using the Atom editor to develop their OCaml code, students using other editors can skip this step. The second part is for all students who want to use the course `Lib` module from a REPL. 

> **NOTE**: The instructions below assume the student is enrolled in CSCI 1103 Computer Science 1 Honors. Students enrolled in CSCI 3366 Programming Languages should make the obvious adjustments.

#### 0. Cloning this lib Repository

The first step is to clone this course lib repository. We assume that you've already made a course home folder `csci1103` or `csci3366` in your home directory. If you've named it something else or placed it someplace else, you'll need to make adjustments to several of the commands below. In a Unix shell type

```bash
> cd
> cd csci1103    # or cd csci3366
> git clone https://github.com/BC-CSCI1103/lib.git     # or BC-CSCI3366
```

#### 1. Installing Two Patches to Atom's Repl Package

If you are using Atom as your development environment **and** you would like to use Atom's [Repl Package](https://atom.io/packages/repl) which allows you to run an OCaml REPL from within the editor, you'll need to install two patches to the Repl Package by following the instructions below. **NOTE:** these instructions can only be carried out *after* both Atom and its Repl package have been installed. 

> **TMI**: 
>
> + The `ReplView.coffee` file distributed with Atom's Repl Package causes the OCaml formatting and highlighting support to attempt to parse text in the REPL window as though it were OCaml source code. Of course it isn't. The copy of `ReplView.coffee` included here fixes that.
> + The `replOcaml.js` file distributed with Atom's Repl Package attempts to use a Python prompt in an OCaml REPL session. The copy of `replOcaml.js` included here fixes that.

```bash
> cd
> cd csci1103/lib      # or csci3366
> cp ReplView.coffee ~/.atom/packages/Repl/lib/Repl-View/
> cp replOcaml.js ~/.atom/packages/Repl/Repls/
```

#### 2. Installing the Lib Module in REPLs

The `Lib` module has a number of resources that are useful in the course. Problem sets will generally be distributed with a copy of the `Lib` module in `src/lib/` and the dune build system will be able to find the library for code run via `dune exec`. In some cases, it's reasonable to want to use the `Lib` module from code evaluated in a REPL. The easiest way to distribute the course `Lib` module for access from a REPL is to define a copy of the `Lib` module within OCaml's REPL startup file `~/.ocamlinit`. This file is automatically loaded whenever a REPL boots up. 

```bash
> cd
> cd csci1103/lib    #   or csci3366
> cp ocamlinit ~/.ocamlinit
```

**NOTE**: Don't overlook the period in the last line.