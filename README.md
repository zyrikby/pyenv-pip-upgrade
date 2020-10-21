## Description
This is a [pyenv](https://github.com/pyenv/pyenv/) plugin that allows you to update all packages of particular or all pyenv environments excluding *system*. It supports both *conda*- and *pip*-based environments. You can read more about the plugin and its implementation details in [this article](https://zhauniarovich.com/post/2020/2020-10-why-pyenv-pip-upgrade/).


## Usage
If you want to update all packages in all pyenv environments, execute the following command

```console
$ pyenv pip-upgrade --all
```

However, more often we need to update packages of particular environments. This plugin allows updating packages of selected environments. For instance, the following command will update 3 environments `3.9.0`, `3.9.0/envs/pyenv_test`, and `miniconda3-latest/envs/myenv`: 

```console
$ pyenv pip-upgrade 3.9.0 3.9.0/envs/pyenv_test miniconda3-latest/envs/myenv
```

By default, the packages of an environment are updated using one `pip install --upgrade` command, i.e., if, e.g., the *cowsay* and *six* packages need to be updated, the command to update them will be `pip install --upgrade cowsay six`. The new [***2020 pip resolver***](https://pip.pypa.io/en/stable/user_guide/#changes-to-the-pip-dependency-resolver-in-20-2-2020) will check dependencies of these packages, and if there are conflicts it will generate an error.

However, it is possible to run update packages sequentially using `--sequential` *pip-upgrade* option. In this case, the packages will be updated one by one as in it is done in the [original stackoverflow answer](https://stackoverflow.com/a/3452888/1108213), and the most recently updated package will override conflicting dependencies.

The plugin supports autocompletion. Press `<TAB>` twice to see available choices. 


## Installation
In order to install the plugin you need at first install and configure [*pyenv*](https://github.com/pyenv/pyenv/). Then, just execute the following command from your terminal:

```console
$ git clone https://github.com/zyrikby/pyenv-pip-upgrade.git $(pyenv root)/plugins/pyenv-pip-upgrade
```

This command will clone the repository of plugin into the *pyenv* plugins directory. After this, *pyenv* will be also responsible for updating the plugin to the latest version if it appears.


## Inspiration
The development of this plugin has been inspired by the following projects/articles:

1. [pyenv-pip-update](https://github.com/massongit/pyenv-pip-update) --- a *pyenv* plugin to update all environments at once
2. [stackoverflow answer](https://stackoverflow.com/a/3452888/1108213) --- stackoverflow answer how to update all packages using *pip*
3. [Bash Strict Mode](http://redsymbol.net/articles/unofficial-bash-strict-mode/) --- article about bash strict mode
