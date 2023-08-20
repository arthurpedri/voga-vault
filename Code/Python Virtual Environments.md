A self-contained directory tree that contains a Python installation for a particular version of Python, plus a number of additional packages.

## Creating Virtual Environments
```bash
python -m venv directory-for-env
source directory-for-env/bin/activate
```
- This will create and activate the environment.
```bash
deactivate
```
- Will deactivate a virtual environment.
## Separation from source code
- The virtual environments should be separate from the source code, as they are dependent on the machine.
- The usual place to keep them is in `~/.virtualenvs/`
- The dependencies that a project needs should be stored in a file on the source code, and can be used to create an appropriate virtual environment on any machine.
## Managing Packages
- You can manage packages just as you would globally on a venv using **pip**.
```bash
python -m pip install package
```
- The `-m` will ensure that the python interpreter that is calling pip is the one in our virtual environment.