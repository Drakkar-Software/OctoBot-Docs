OctoBot 0.4
===========

About OctoBot 0.4
-----------------

OctoBot 0.4 is a complete rework of OctoBot, while it doesn't change a
lot on the appearance (for now), its core engine is completely
different.

With 0.4, OctoBot uses an asynchronous producer/consumer design. This
enables deep optimizations by removing every downtime and therefore
taking every signal opportunity as soon as possible without being
overwhelmed by information. This is ideal for websocket connexions and
enables the full potential of any strategy.

To go even further on the optimization path, OctoBot is now using
[Cython](https://cython.org/) to compile its CPU intensive processes
into efficient C code and increase its performances.

What's new on OctoBot 0.4 ?
----------------------------

### High speed trading

Thanks to its increased performances, OctoBot is now suitable for
arbitrage, leverage trading, future trading, order book analysis and
more. Trading on these products is not available yet but it will come in
the the near future with dedicated trading strategies.

This is the main feature of this new version and is paving the way to
many more trading strategies and possibilities.

### Inifinite customization

Each and every OctoBot interface is now a tentacle, meaning it can
easily be customized and improved. This makes it easy to plug a anything
into OctoBot from a system getting data from another website to a
websocket exchange connexion or even an sms command interface, basically
anything.

### Improved backtesting

Starting from 0.4, OctoBot will be able to process backtestings with all
of its price data based trading strategies. Multi-exchanges backtestings
is also possible and accurate.

### Improved web interface

OctoBot's web interface now has a much stronger server side, this
enabled more reactivity and a smoother user experience.

From Octobot 0.3 to 0.4
-----------------------

### OctoBot 0.4 installation

#### OctoBot executable

Download and start the OctoBot 0.4.0 executable for your computer from
<https://github.com/Drakkar-Software/OctoBot/releases>.

The first start will setup your OctoBot environment and download
tentacles.

#### OctoBot CLI

To install OctoBot 0.4, the easiest way is to use [the OctoBot
CLI](https://pypi.org/project/OctoBot-CLI/) to install OctoBot 0.4
either using docker or python directly.

1.  Install octobot-cli using the following command:

    ``` bash
    python -m pip install octobot_cli
    ```

2.  Go to the directory you want your OctoBot0.4 to be installed
3.  Now two possibilities: you can install OctoBot using python (pip and
    virtual env), it is preferred way for Windows users or using docker
    if you are familiar with it.

For a python installation open a terminal and type in:

``` bash
octobot_cli install --python
```

For a docker installation, open a terminal and type in:

``` bash
octobot_cli install --docker
```

Note: if you are on an arm architecture (like on raspberry pie), add the
`--arm` argument to the docker command.

1.  Start your OctoBot using the following command: Python
    installations:

    ``` bash
    octobot_cli start
    ```

    Docker installations:

    ``` bash
    octobot_cli start --docker
    ```

    ### OctoBot 0.4 update To update your OctoBot, use the following
    command: Python installations:

    ``` bash
    octobot_cli update
    ```

    Docker installations:

    ``` bash
    octobot_cli update --docker
    ```

    This will update your OctoBot with its dependencies and tentacles

### Manual installation

**With the OctoBot executable**

Download and start the latest OctoBot 0.4.0 executable for your computer
from <https://github.com/Drakkar-Software/OctoBot/releases>.

The first start will setup your OctoBot environment and download
tentacles.

**With Docker**

1.  Get the latest Octobot 0.4 image:

    ``` bash
    docker pull drakkarsoftware/octobot:0.4.0-stable
    ```

2.  Run it via

    ``` bash
    docker run -it -d --name Octobot -p 5001:5001 -v $(pwd)/user:/octobot/user -v $(pwd)/tentacles:/octobot/tentacles -v $(pwd)/logs:/octobot/logs drakkarsoftware/octobot:0.4.0-stable
    ```

3.  Follow the [docker help
    docs](../Installation/With-Docker.md#how-to-look-at-octobot-logs) if you need
    more details about how to use OctoBot with Docker.

**With Python**

1.  Clone the [OctoBot 0.4
    branch](https://github.com/Drakkar-Software/OctoBot/tree/0.4.0)

    ``` bash
    git clone -b 0.4.0 https://github.com/Drakkar-Software/OctoBot
    ```

2.  Install the requirements via

    ``` bash
    pip install --prefer-binary -Ur requirements.txt
    ```

    **--prefer-binary** is important here otherwise you will have to
    recompile every module: it requires a c++ compiler and can be very
    slow.

3.  Start your OctoBot using

    ``` bash
    python start.py
    ```

**Using CentOS**

Requirements

``` bash
yum -y update
yum install -y git wget sqlite-devel screen
yum -y groupinstall "Development Tools"
yum -y install openssl-devel bzip2-devel libffi-devel
yum install -y screen
cd /root
wget https://www.python.org/ftp/python/3.10.11/Python-3.10.11.tgz
tar xvf Python-3.10.11.tgz
cd Python-3.10*/
./configure --enable-loadable-sqlite-extensions && make && sudo make install
```

OctoBot

``` bash
git clone https://github.com/Drakkar-Software/OctoBot.git
cd OctoBot/
git checkout remotes/origin/0.4.0
python3.10 -m pip install virtualenv
virtualenv venv
source venv/bin/activate
pip install -Ur requirements.txt
python start.py tentacles --install --all
python start.py
```

### Manual update

To update your OctoBot, use the following commands:

``` bash
python -m pip install --prefer-binary -Ur requirements.txt
python start.py tentacles --install --all
```

### OctoBot configuration

OctoBot 0.4 configuration file uses the same format as the 0.3 one and
is also located in **user/config.json**. It is possible to use the same
as a current OctoBot 0.3.

### OctoBot tentacles

OctoBot will automatically download the 0.4 version of its tentacles
during the first launch. Every existing official 0.3 tentacle has an
equivalent in 0.4 with similar configuration options. Some tentacles are
now much more customizable.
