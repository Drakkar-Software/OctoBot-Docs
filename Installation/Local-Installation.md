# Local installation

## Option 1: With the executable

{% embed url="https://www.youtube.com/watch?v=InIGr9nidfc" %}

1. Download the latest version for your system:
   * [Windows](https://release.octobot.online/stable/OctoBot\_windows\_x64.exe)
   * [Linux](https://release.octobot.online/stable/OctoBot\_linux\_x64)
   * [MacOS](https://release.octobot.online/stable/OctoBot\_macos\_x64)
2. Start the downloaded executable. OctoBot opens a terminal and installs its configuration environment and the OctoBot management interface opens automatically.

{% hint style="info" %}
On Windows, you can just double click the executable.

On Linux, first type `chmod +x OctoBot_linux_x64` and then `./OctoBot_linux_x64` in a terminal open next to your downloaded executable to start OctoBot.
{% endhint %}

## Option 2: With Docker

{% embed url="https://www.youtube.com/watch?v=UUzgYNqzNFM" %}

1. If you don't have [Docker](https://www.docker.com/), install it on your system. Here is the docker documentation for [Ubuntu](https://docs.docker.com/engine/install/ubuntu/), [Debian](https://docs.docker.com/engine/install/debian/) et [Raspberry pie](https://phoenixnap.com/kb/docker-on-raspberry-pi/).
2. Download the OctoBot image using the command:\
   `docker pull drakkarsoftware/octobot:stable`
3. Start your OctoBot using the command:\
   `docker run -itd --name OctoBot -p 80:5001 -v $(pwd)/user:/octobot/user -v $(pwd)/tentacles:/octobot/tentacles -v $(pwd)/logs:/octobot/logs drakkarsoftware/octobot:stable`

The management interface of your OctoBot is available on port 5001 of your system. http://localhost:5001/ or http://ip-address:5001/

Find all the details regarding the docker installation on [the dedicated page](../installation/with-docker/)

## Option 3: From the source code

Deploy your OctoBot from the code in to be able to use a local Python environment, edit or audit the source code.

1. If you don't already have Python, install [Python in version 3.10](https://www.python.org/downloads/release/python-31011/).
2. Clone the OctoBot repository\
   `git clone https://github.com/Drakkar-Software/OctoBot`
3. Install the Python dependencies\
   `cd OctoBot`\
   `python3 -m pip install -Ur requirements.txt`
4. Start your OctoBot using this command:\
   `python3 start.py`

The management interface of your OctoBot is available on port 5001 of your system. http://localhost:5001/ or http://ip-address:5001/

Find all the details regarding the source code installation on [the dedicated page](../installation/With-Python-only/)
