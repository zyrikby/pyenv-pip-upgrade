## Description
This is a [pyenv](https://github.com/pyenv/pyenv/) that allows you to update all packages in particular or all pyenv environments excluding *system*. It supports both *conda*- and *pip*-based environments.

## Usage
If you want to update all packages in all pyenv environments, execute the following command

```console
$ pyenv pip-upgrade --all
```

However, more often we need to update packages of particular environments. This plugin allows updating packages of selected environments. For instance, the following command will update 3 environments `3.9.0`, `3.9.0/envs/pyenv_test`, and `miniconda3-latest/envs/myenv`: 

```console
$ pyenv pip-upgrade 3.9.0 3.9.0/envs/pyenv_test miniconda3-latest/envs/myenv
```

## Installation
In order to install the plugin you need at first install and configure [*pyenv*](https://github.com/pyenv/pyenv/). Then, just execute the following command from your terminal:

```console
$ git clone https://github.com/zyrikby/pyenv-pip-upgrade.git $(pyenv root)/plugins/pyenv-pip-upgrade
```

This command will clone the repository of plugin into the *pyenv* plugins directory. After this, *pyenv* will be also responsible for updating the plugin to the latest version if it appears.