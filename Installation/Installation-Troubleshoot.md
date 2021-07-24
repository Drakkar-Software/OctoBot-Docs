Troubleshoot
============

Cannot connect to host www.tentacles.octobot.online:443
-------------------------------------------------------

[![tentacles url error](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/troubleshoot-tentacles-url-error.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/troubleshoot-tentacles-url-error.png)

``` bash
octobot_tentacles_manager.api.util.tentacles_management Exception during InstallWorker processing: Cannot connect to host www.tentacles.octobot.online:443 ssl:default [No address associated with hostname] (ClientConnectorError)
```

The tentacles server URL has changed, there is no more leading "www". Starting from 0.4.0b6, OctoBot uses the latest URL. To use OctoBot previous versions, please first set this environment variable before downloading tentacles:

On Unix systems

``` bash
$ export TENTACLES_URL="https://tentacles.octobot.online/repository/tentacles/officials/packages/full/base/0.4.0b4/any_platform.zip"
$ python3 start.py tentacles --install --all
```

On Windows systems

``` bash
$ SET TENTACLES_URL=https://tentacles.octobot.online/repository/tentacles/officials/packages/full/base/0.4.0b4/any_platform.zip
$ python3 start.py tentacles --install --all
```

Using Docker

``` bash
$ docker run -itd --name OctoBot -p 80:5001 -e TENTACLES_URL="https://tentacles.octobot.online/repository/tentacles/officials/packages/full/base/0.4.0b4/any_platform.zip" -v $(pwd)/user:/octobot/user -v $(pwd)/tentacles:/octobot/tentacles -v $(pwd)/logs:/octobot/logs drakkarsoftware/octobot:stable
```

Where 0.4.0b4 is your OctoBot version.

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
