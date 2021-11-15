---
description: Setting up the recommended OctoBot development environment
---

# OctoBot developer installation

{% hint style="info" %}
This page is referring to OctoBot in versions superior to 0.4.0.
{% endhint %}

* ****[**Install OctoBot requirements**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/guides/dev-environment-setup#install-octobot-requirements)****
* ****[**Cloning OctoBot repositories**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/guides/dev-environment-setup#cloning-octobot-repositories)****
* ****[**Setting up the IDE**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/guides/dev-environment-setup#setting-up-the-ide)****
* ****[**create starting scripts in pyCharm**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/installation/developer-installation/full-developer-installation#create-starting-scripts-in-pycharm)****
* ****[**start OctoBot in pyCharm**](https://app.gitbook.com/s/XGhS0OJcF37WFUAtCJrB/c/K2S34tUZ8NdXf7pYP47C/installation/developer-installation/full-developer-installation#start-octobot-in-pycharm)****

## Install OctoBot requirements

**Download and install:**

* IDE: [PyCharm](https://www.jetbrains.com/pycharm/)
* SCM: [Git](https://git-scm.com/downloads)
*   we also use [GitKraken](https://www.gitkraken.com/git-client) to easily manage

    OctoBot's multiple repos, this is just a quality of life

    improvement and is not necessary.
* Language: [Python 3.8](https://www.python.org/downloads/)

#### additional dependencies for Windows

* download [Visual Studio build tools](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) and install "Desktop development with C++"

![](<../../.gitbook/assets/image (6).png>)

![](<../../.gitbook/assets/image (1).png>)

#### additional Dependencies for Mac

* install [GCC](https://discussions.apple.com/thread/8336714)

## OctoBot repositories

### Cloning OctoBot repositories with git

* open a terminal in your project folder and execute the following commands to download the repos

```bash
git clone --branch dev https://github.com/Drakkar-Software/OctoBot.git
git clone --branch dev https://github.com/Drakkar-Software/OctoBot-Tentacles.git
git clone https://github.com/Drakkar-Software/OctoBot-Trading
git clone https://github.com/Drakkar-Software/OctoBot-evaluators
git clone https://github.com/Drakkar-Software/OctoBot-Services
git clone https://github.com/Drakkar-Software/OctoBot-Backtesting
git clone https://github.com/Drakkar-Software/OctoBot-Tentacles-Manager
git clone https://github.com/Drakkar-Software/OctoBot-Commons
git clone https://github.com/Drakkar-Software/Async-Channel
git clone https://github.com/Drakkar-Software/trading-backend
```

* now you should have all the OctoBot repos in one folder

![](<../../.gitbook/assets/image (8).png>)

### Manage repositories with GitKraken

* open each folder in GitKraken

![](<../../.gitbook/assets/image (9).png>)

* add your project directory (the folder where all repo folders are located)

![](<../../.gitbook/assets/image (3).png>)

* now add each folder

![](<../../.gitbook/assets/image (21).png>)

* Now you have all repositories open as tabs and you can switch between branches

### switch to experimental branches

* You can explore and switch to different branches by double-clicking on the branch name for each repository, or right click "reset to this commit".

![](<../../.gitbook/assets/image (18).png>)

## Setting up the IDE

We recommend using [PyCharm](https://www.jetbrains.com/pycharm/) to navigate through the OctoBot projects. This IDE will allow you to open and navigate through the multiple OctoBot repositories and make your OctoBot run setup use the code directly from the cloned repos using the project dependencies.

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

{% hint style="warning" %}
Do not install the requirements related to the previously downloaded repositories or your python runner will use them instead of your local code version.
{% endhint %}

* For each OctoBot's repository: install missing dependencies in requirements.txt and dev\_requirements.txt, except the OctoBot packages

```
pip install -r Octobot/requirements.txt
pip install -r OctoBot-Backtesting/requirements.txt
pip install -r OctoBot-Commons/requirements.txt
pip install -r OctoBot-evaluators/requirements.txt
pip install -r OctoBot-Services/requirements.txt
pip install -r OctoBot-Tentacles-Manager/requirements.txt
pip install -r Octobot/OctoBot-Trading.txt
```

* remove octobot pip packages to use the packages from your project directory

```
pip uninstall -y OctoBot-Backtesting OctoBot-Trading Async-Channel OctoBot-Evaluators OctoBot-Commons OctoBot-Tentacles-Manager OctoBot-Services trading-backend
```

## create starting scripts in pyCharm

Create PyCharm run configurations using the previously created virtual env (with all the dependencies installed) for each way you want to start python commands (running OctoBot, running tests, etc).

[![run configuration](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki\_resources/run\_config.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki\_resources/run\_config.png)

### OctoBot starting script

{% hint style="info" %}
this script will run OctoBot and apply all changes made to all repositories except the OctoBot-Tentacles folder
{% endhint %}

* click on Add Configuration

![](<../../.gitbook/assets/image (12).png>)

now add a new python script

![](<../../.gitbook/assets/image (20).png>)

### install OctoBot-Tentacles and run OctoBot script

{% hint style="info" %}
this script will install the OctoBot-Tentacles folder and run Octobot with all your changes applied from all repositories.
{% endhint %}

#### Create the following three scripts:

* **Script to create an installable OctoBot-Tentacles package **

![](<../../.gitbook/assets/image (7).png>)

* **Script to install OctoBot-Tentacles package**

![](<../../.gitbook/assets/image (14).png>)

* **Script to zip, install and run in one go**

![](<../../.gitbook/assets/image (2).png>)

## start OctoBot in pyCharm

* You can now run and debug the whole OctoBot project and its repositories by clicking on the play button, or on the debugging button to run the debugger

![](<../../.gitbook/assets/image (13).png>)
