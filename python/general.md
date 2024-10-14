# General development stuff for Python

## Running module vs. a script
Write some stuff about the shebang line and ```if __name__ == '__main__':```
idiom. The former is responsible for running the script from the
command line (most likely, you'll have to ```chmod u+x file_to_run.py```
first in order to actually run it); the latter is for prohibiting execution
of statements when the file is loaded as a module - either via interpreter
session or as a module within other source file.

Both can coexist in the same file (i.e., module) with out breaking stuff.

## How to 'properly' exit a Python program?
Diffs between ```import sys; sys.exit(main())``` and ```raise SystemExit(main())```.
As shown above, we can't use ```sys.exit()``` without first introducing
its module name into the global namespace, even though the docs claim
that ```sys``` is always available (see below).

```sys.exit()``` raises ```SystemExit()``` exception. From a conceptual
point of view, they are the same. The difference is in 'availability' of
the ```sys``` module itself. 'Always available' means that you can raise
```SystemExit()``` without importing ```sys``` beforehand. In short scripts
or for demonstration purposes, it saves you one line of typing; if you
do something useful with the command line, say passing the ```argv[]```
arguments, you need for the ```sys``` module to be imported either way.
So, in those cases ```import sys``` is inescapable.
