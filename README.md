# calcium-roi-analysis

Detection and analysis of rois in calcium imaging

## Setting Up your Development Environment

This instructions are for MacOS, while they should roughly be the same for Windows and Linux, they are untested in those environments:

1. Homebrew

[Homebrew](https://brew.sh) is a popular package manager for MacOS

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

2. `pyenv`

### Installation

[`pyenv`](https://github.com/pyenv/pyenv) allows you to run and manage multiple versions of Python, all in isolations from your system's Python.
If this is your first time using `pyenv` you can learn more about isuing it in [this blog post](https://realpython.com/intro-to-pyenv/#exploring-pyenv-commands)

`brew install pyenv`

Append `pyenv init` to bash's profile

`$ echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n eval "$(pyenv init -)"\nfi' >> ~/.bash_profile`

And restart your SHELL

`exec "$SHELL"`

### List versions of Python available to install

`pyenv install --list`

### Install most recent stable version

A stable version means there is no `-dev` of `-rc` after the name. For instance run

`pyenv install 3.8.1`

### Activate global environment to that

`pyenv global 3.8.0`

### Listing available versions to the system

`pyenv versions`

### Configuring a local environment

When you are in a folder, you can configure the version of the Python that is activated when you are calling Python within that folder by calling for instance `pyenv local 3.8.0` within your directory.

This will create a hidden file `.python-version` in the current directory.

3. `pipx`

[PIPX](https://github.com/pipxproject/pipx) allows you to install Python (and Ruby) CLI utilities in their own environment, without contaminating your global environment

### Installation

`python -m pip install pipx`

4. Jupyter -- Skip if using VSCode (highly recommended)

We will install Jupyter in it's own environment using `pipx`

`pipx install jupyter --include-deps`

5. Poetry

Poetry handles dependency- and virtual-environment-management in a way that’s very intuitive (to me), and fits perfectly with my desired workflow.

`pipx install poetry`

### Configure poetry to create virtual environments inside the project's root directory

`poetry config virtualenvs.in-project true`

### Making sure that Poetry is using Pyenvs python

`poetry env use $(pyenv which python)`

### Install ipython kernel spec

`poetry run python -m ipykernel install --user --name=calcium-roi-analysis`
