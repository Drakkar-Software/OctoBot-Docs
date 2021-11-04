---
description: Setting up the recommended OctoBot development environment
---

# OctoBot developer installation

{% hint style="info" %}
This page is referring to OctoBot in versions superior to 0.4.0.
{% endhint %}

* ****[**Install OctoBot requirements**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/guides/dev-environment-setup#install-octobot-requirements)****
* ****[**Cloning OctoBot repositories**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/guides/dev-environment-setup#cloning-octobot-repositories)****
* ****[**OctoBot repositories**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/guides/dev-environment-setup#octobot-repositories)****
* ****[**Setting up the IDE**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/guides/dev-environment-setup#setting-up-the-ide)****
* ****[**create starting scripts in pycharm**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/installation/developer-installation/full-developer-installation#create-starting-scripts-in-pycharm)****
* ****[**start OctoBot in pycharm**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/installation/developer-installation/full-developer-installation#start-octobot-in-pycharm)****

## Install OctoBot requirements

**Download and install:**

* IDE: [PyCharm](https://www.jetbrains.com/pycharm/)
* SCM: [Git](https://git-scm.com/downloads)
*   we also use [GitKraken](https://www.gitkraken.com/git-client) to easily manage

    OctoBot's multiple repos, this is just a quality of life

    improvement and is not necessary.
* Language: [Python 3.8](https://www.python.org/downloads/)

#### Dependencies for Windows

* download [Visual Studio build tools](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) and install "Desktop development with C++"

![](<../../.gitbook/assets/image (6).png>)

![](<../../.gitbook/assets/image (1).png>)

#### Dependencies for Mac

* install [GCC](https://discussions.apple.com/thread/8336714)

## Cloning OctoBot repositories

* Clone each OctoBot repository using the dev branch when specified.

### Cloning script for unix setups

A script to install these git repos on a unix setup

```bash
#!/bin/bash

readonly REMOTE_DEVBRANCH="remotes/origin/dev"
readonly DEVBRANCH="dev"
readonly BASEDIR=$(dirname "$0")

branch_work() {
  dir=$1
  devbranch=$2
  branch=$(cd $BASEDIR/$dir && git name-rev --name-only HEAD)
  if $devbranch; then
    if [ $branch == $REMOTE_DEVBRANCH ]; then
      echo "[WARN] Already on branch: $branch "
      echo "[INFO] Delete Folder: $dir - if you would like to have clean $dir project"
    else
      (cd $dir; git checkout $DEVBRANCH)
    fi
  fi
}

project_work() {
  url=$1
  devbranch=$2
  dir=$(basename -s .git "$url")
  echo "Check Dir $BASEDIR/$dir"
  if [ -d $BASEDIR/$dir ]; then
    echo "[WARN] Directory: $dir exists!"
    branch_work $dir $devbranch
  else
    echo "----- $dir -----"
    git clone $url
    branch_work $dir $devbranch
    echo "----- END $dir -----"
  fi
}

#Uses dev branch: true/false
project_work https://github.com/Drakkar-Software/OctoBot.git true
project_work https://github.com/Drakkar-Software/OctoBot-Tentacles.git true
project_work https://github.com/Drakkar-Software/OctoBot-Trading false
project_work https://github.com/Drakkar-Software/OctoBot-evaluators false
project_work https://github.com/Drakkar-Software/OctoBot-Services false
project_work https://github.com/Drakkar-Software/OctoBot-Backtesting false
project_work https://github.com/Drakkar-Software/OctoBot-Tentacles-Manager false
project_work https://github.com/Drakkar-Software/OctoBot-Commons false
project_work https://github.com/Drakkar-Software/Async-Channel false
```

### Cloning OctoBot repositories with GitKraken

* open up GitKraken and press on Clone a repo

![](<../../.gitbook/assets/image (4).png>)

*   Clone the repository into the preferred destination

    and repeat that step for all repositories [below](octobot-developer-installation.md#octobot-repositories)

![](<../../.gitbook/assets/image (18).png>)

* now you should have all the Octobot modules in one folder

![](<../../.gitbook/assets/image (8).png>)

#### OctoBot repositories

OctoBot code is split in multiple repositories:

*   [https://github.com/Drakkar-Software/OctoBot](https://github.com/Drakkar-Software/OctoBot) (dev branch) for the

    main program initialization, backtesting and strategy optimizer setup as well as community data management.
*   [https://github.com/Drakkar-Software/OctoBot-Tentacles](https://github.com/Drakkar-Software/OctoBot-Tentacles) (dev branch)

    for tentacles: evaluators, strategies, trading modes, interfaces, notifiers, external data feeds (twitter, telegram etc), backtesting data formats management and exchange specific behaviors.
*   [https://github.com/Drakkar-Software/OctoBot-Trading](https://github.com/Drakkar-Software/OctoBot-Trading) for everything

    trading and exchange related: exchange connections, exchange data

    fetch and update, orders, trades and portfolios management.
*   [https://github.com/Drakkar-Software/OctoBot-evaluators](https://github.com/Drakkar-Software/OctoBot-evaluators) for

    everything related to evaluators and strategies.
*   [https://github.com/Drakkar-Software/OctoBot-Services](https://github.com/Drakkar-Software/OctoBot-Services) for

    everything related to interfaces: graphic (web) and text(telegram), notifications push and social analysis data management: update engine to handle new data from an external feed (ex: twitter) when it gets available.
*   [https://github.com/Drakkar-Software/OctoBot-Backtesting](https://github.com/Drakkar-Software/OctoBot-Backtesting) for the

    backtesting engine and scheduling as well as historical data collection unified storage management.
*   [https://github.com/Drakkar-Software/OctoBot-Tentacles-Manager](https://github.com/Drakkar-Software/OctoBot-Tentacles-Manager) for

    tentacles installation, updates and interactions: get a tentacle documentation, configuration or it's dependencies.
*   [https://github.com/Drakkar-Software/OctoBot-Commons](https://github.com/Drakkar-Software/OctoBot-Commons) for common

    tools and constants used across each above repository.
*   [https://github.com/Drakkar-Software/Async-Channel](https://github.com/Drakkar-Software/Async-Channel) which is used by

    OctoBot as a base framework for every data transfer within the bot. This allows a highly optimized and scalable architecture that adapts to any system while using a very low amount of CPU and RAM.

### Manage repositories in GitKraken

* open each folder in GitKraken

![](<../../.gitbook/assets/image (9).png>)

* add your project directory (the folder where all module folders are located)

![](<../../.gitbook/assets/image (3).png>)

* now add each folder

![](<../../.gitbook/assets/image (20).png>)

* Now you have all repositories open as tabs and you can switch between branches

### switch to dev branches

* By default you downloaded all master branches. You can switch to the dev branches by double-clicking on the dev branch for each repository

![](../../.gitbook/assets/image.png)

## Setting up the IDE

We recommand using [PyCharm](https://www.jetbrains.com/pycharm/) to navigate through the OctoBot projects. This IDE will allow you to open and navigate through the multiple OctoBot repositories and make your OctoBot run setup use the code directly from the clonned repos using the project dependencies.

* Open Pycharm and open the folder where all the OctoBot repositories are.
*   In File/Settings/Project/Python Interpreter: select your installed python3.8 and create a new virtual environment through PyCharm.

    [![python interpreter](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki\_resources/python\_interpreter.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki\_resources/python\_interpreter.png)

### Add OctoBot modules

This will allow your PyCharm python runner to use your OctoBot repositories as source code directly. Thanks to this you will be able to edit any file in any repo and it will be taken into account in your other PyCharm run profiles runners from other open OctoBot repo. This is useful when running tests. If you skip this, you will need to install every OctoBot module with pip and won't be able to edit their code.

### Add OctoBot modules with PyCharm Pro

*   In File/Settings/Project/Python Dependencies: For each repository: check its required OctoBot repository dependency.&#x20;

    [![python dependencies](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki\_resources/python\_dependencies.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki\_resources/python\_dependencies.png)

### Add OctoBot modules with PyCharm Community

Go to File -> Settings and add your OctoBot module folders as a project source![](<../../.gitbook/assets/image (5).png>)

### Install Octobot dependencies

* For each OctoBot's repository: install missing dependencies in requirements.txt and dev\_requirements.txt.

{% hint style="warning" %}
Do not install the requirements related to the previously downloaded repositories or your python runner will use them instead of your local code version.
{% endhint %}

## create starting scripts in pycharm

\* Create PyCharm run configurations using the previously created virtual env (with all the dependencies installed) for each way you want to start python commands (running OctoBot, running tests, etc).

[![run configuration](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki\_resources/run\_config.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki\_resources/run\_config.png)

### OctoBot starting script

{% hint style="info" %}
this script will run OctoBot and apply all changes made to all repositories except the OctoBot-Tentacles folder
{% endhint %}

* click on Add Configuration

![](<../../.gitbook/assets/image (12).png>)

now add a new python script

![](<../../.gitbook/assets/image (19).png>)

### install OctoBot-Tentacles and run OctoBot script

{% hint style="info" %}
this script will install the OctoBot-Tentacles folder and run Octobot with all your changes applied from all repositories.
{% endhint %}

#### create the following three scripts:

* **Script to create an installable OctoBot-Tentacles package **

![](<../../.gitbook/assets/image (7).png>)

* **Script to install OctoBot-Tentacles package**

![](<../../.gitbook/assets/image (14).png>)

* **Script to zip, install and run in one go**

![](<../../.gitbook/assets/image (2).png>)

## start OctoBot in pycharm

* You can now run and debug the whole OctoBot project and its repositories by clicking on the play button, or on the debugging button to run the debugger

![](<../../.gitbook/assets/image (13).png>)
