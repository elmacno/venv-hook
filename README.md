# venv-hook

Automatic python virtualenv loading and unloading

## Installation

Clone this repository somewhere:

```sh
git clone https://github.com/elmacno/venv-hook.git ~/.venv-hook
```

Then follow the instructions for bash and/or zsh below.

> :info: **How do I tell which one I'm using?**: You can check the content of `$BASH_VERSION` environment variable (for `BASH`) or `$ZSH_VERSION` (for `ZSH`). If they have any value, then you are using that shell.

### For `BASH`

Add the following at the end of your `$HOME/.bashrc` file:

```sh
. $HOME/.venv-hook/venv-hook
```

### For `ZSH`

Add the following at the end of your `$HOME/.zshrc` file:

```sh
. $HOME/.venv-hook/venv-hook
```

## Usage

After you create your python's virtual environment using `virtualenv` such as:

```sh
virtualenv /path/to/virtualenvironments/my-shiny-virtualenv
```

You can then add a `.virtualenvrc` file under the directory you will use that virtual environment. The contents of that file should be the full, absolute path to said virtual environment:

```
# .virtualenvrc
/path/to/virtualenvironments/my-shiny-virtualenv
```

You can create the `.virtualenvrc` file by running:

```sh
echo /path/to/virtualenvironments/my-shiny-virtualenv > .virtualenvrc
```

If you are using relative paths to create your virtual environment, you need to convert it to an absolute path:

```sh
echo $PWD/relative/path/to/virtualenvironments/my-shiny-virtualenv > .virtualenvrc
```

And that's it! When you switch to a directory that contains a `.virtualenvrc`, that environment will be automatically activated. This will also work for any of the subdirectories under the parent directory with that `.virtualenvrc` file.

And when switching out of that directory to another that doesn't contain a `.virtualenvrc` file in any of the parent directories, your virtual environment will be deactivated.
