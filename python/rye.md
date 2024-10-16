# `rye` - Rust's `cargo` experience in Python

## Creating a project
- To create a package, run:
```
$ rye init project-name
```

- For an executable script, run:
```
$ rye init --script project-name
```

__NOTE:__ the `--script` option creates three additional files within
the project's directory structure:
- `.venv/bin/project-name`
- `.venv/lib/pythonX.Y/site-packages/project-name-0.1.0.dist-info/entry_points.txt`,
where `pythonX.Y` stands for the Python version `rye` has used to
create the project with, e.g., `python3.12`
- `src/project-name/__main__.py`

The purpose of these is to create an executable script that you can
run either via `rye run project-name` or, when the `.venv` dir has
been sourced manually, via `project-name`.

## Sourcing .venv
`cd`-ing into the project's directory activates the virtual
environment automatically:
```
$ cd project-name
$ python -c 'import sys; print(sys.prefix)'
/path/to/your/project-name/.venv
```

Why bother, then, with `source .venv/bin/activate`? Convenience. Each
invocation of the script has to go through `rye run`, e.g.:
```
$ pytest
$ zsh: command not found: pytest
$ rye run pytest
# ... runs tests
```

Activating the virtual environment manually allows one to invoke the
script directly from the command line, like so:
```
$ pytest
zsh: command not found: pytest
$ source .venv/bin/activate
(project-name) $ pytest
# ... runs tests
```
