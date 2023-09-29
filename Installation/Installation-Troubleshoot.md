Troubleshoot
============

Windows
-------

### Time synchronization

This issue happens when error messages such as `'recvWindow' must be less than ...` appear.

Open an administrator terminal (`Win + X` then `A`) and type:

``` bash
net stop w32time
net start w32time
w32tm /resync
w32tm /query /status
```

Code from [serverfault.com](https://serverfault.com/questions/294787/how-do-i-force-sync-the-time-on-windows-workstation-or-server)

Another solution found by @alpi on discord channel: [timesynctool.com](http://www.timesynctool.com)

### OctoBot freeze

When running OctoBot on Windows, clicking into the OctoBot terminal (Powershell or Cmd) can freeze the log output and therefore freeze OctoBot execution (OctoBot will be waiting for the log to be published to continue).

To fix this issue, untick the "QuickEdit Mode" in your terminal properties and restart it.

[![Powershell](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/powerShellEditMode.jpg){width="400px"}](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/powerShellEditMode.jpg)

[![Cmd](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/cmdQuickEdit.jpg){width="400px"}](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/cmdQuickEdit.jpg)

To open the properties menu, right click on the terminal window header and select "properties".

CentOS
------

### Install OctoBot on CentOS

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
python3.10 -m pip install virtualenv
virtualenv venv
source venv/bin/activate
pip install -Ur requirements.txt
python start.py
```

Linux
-----

### Time synchronization

This issue happens when error messages such as `'recvWindow' must be less than ...` appear.

On Debian or Ubuntu, open a terminal and type:

``` bash
sudo service ntp stop
sudo ntpd -gq
sudo service ntp start
```

Requires `ntp` package installation `sudo apt-get install ntp`.

Code from
[askubuntu.com](https://askubuntu.com/questions/254826/how-to-force-a-clock-update-using-ntp#256004).

### Installation

During pip install if you have SSL problems, open a terminal and type

``` bash
pip3 install service_identity --force --upgrade
```
