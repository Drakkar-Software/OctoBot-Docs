# Developer installation

## Requirements

* Python 3.8 ([download](https://www.python.org/downloads/))
* Git ([Download](https://git-scm.com/downloads))

## Instructions

### Windows

**Python3.8 has to be in environment variable** :

During [python install](https://www.python.org/downloads) check _add to environment var_ checkbox.

Open a command line and type :

```bash
git clone https://github.com/Drakkar-Software/OctoBot -b dev
cd OctoBot
python3 -m pip install -Ur requirements.txt
python3 start.py tentacles --install --all
```

There **python3** is refering to your **Python3.8.X** installation, just adapt the commands to match your setup if any different (might be python, python3, python3.8, etc: it depends on your environment).

Note that python3.8 might be available under the name **python3.8** after this installation.

## Update OctoBot with python only when using OctoBot code directly from dev branch

### Requirements

**Python3.8.X**, **git** and an installed and **functional OctoBot setup** cloned from [OctoBot github repository [https://github.com/Drakkar-Software/OctoBot](https://github.com/Drakkar-Software/OctoBot)]

```bash
$ git pull origin dev
$ python3 -m pip install -Ur requirements.txt
$ python3 start.py tentacles --install --all
```

### Python3

There **python3** is refering to your **Python3.8.X** installation, just adapt the commands to match your setup if any different (might be python, python3, python3.8, etc: it depends on your environment).

## With Repo

Repo is a tool built on top of Git. Repo helps manage many Git repositories.

To create a development OctoBot environment, repo can be used as following :

* [Install repo](https://source.android.com/setup/build/downloading#installing-repo)
* Create a directory for the OctoBot environment
* Create OctoBot developer environment by running

```bash
repo init -u https://github.com/Drakkar-Software/OctoBot-Repo-Manifest.git
```

* Synchronize repositories

```bash
repo sync
```

All required OctoBot projects are now available in the current directory :

```bash
Async-Channel
OctoBot
OctoBot-Backtesting
OctoBot-Commons
OctoBot-Evaluators
OctoBot-Services
OctoBot-Tentacles
OctoBot-Tentacles-Manager
OctoBot-Trading
```

