With Docker
===========

{% hint style="warning" %}
For unix distribution only
{% endhint %}

Installing docker
-----------------

Please follow the instructions
[here](https://docs.docker.com/install/linux/docker-ce/debian/) for a
debian computer.

For a raspberry installation please follow [this
guide](https://phoenixnap.com/kb/docker-on-raspberry-pi).

{% hint style="note" %}
Don't forget to run the following command at the end of the
installation (and logout)
{% endhint %}

``` bash
sudo usermod -aG docker $USER
```

so you don't have this permission denied error each time you use a
docker command : [permission denied while trying to connect to daemon
socket]{.title-ref}.
:::

Running OctoBot
----------------------

{% tabs %}
{% tab title="stable" %}
1.  Download OctoBot
``` bash
docker pull drakkarsoftware/octobot:stable
```
2.  Start OctoBot (for linux x64/x86 and raspberry linux arm64/arm32)
``` bash
docker run -itd --name OctoBot -p 80:5001 -v $(pwd)/user:/octobot/user -v $(pwd)/tentacles:/octobot/tentacles -v $(pwd)/logs:/octobot/logs drakkarsoftware/octobot:stable
```
{% endtab %}
{% tab title="latest (may be unstable)" %}
1.  Download OctoBot latest
``` bash
docker pull drakkarsoftware/octobot:latest
```
2.  Start OctoBot (for linux x64/x86 and raspberry linux arm64/arm32)
``` bash
docker run -itd --name OctoBot -p 80:5001 -v $(pwd)/user:/octobot/user -v $(pwd)/tentacles:/octobot/tentacles -v $(pwd)/logs:/octobot/logs drakkarsoftware/octobot:latest
```
{% endtab %}

### How to look at OctoBot logs ?

``` bash
docker logs OctoBot -f
```

### How to stop OctoBot ?

``` bash
docker stop OctoBot
```

### How to restart OctoBot ?

``` bash
docker restart OctoBot
```

### How to update OctoBot ?

``` bash
docker pull drakkarsoftware/octobot:stable
docker stop OctoBot
docker rm OctoBot
docker run -itd --name OctoBot -p 80:5001 -v $(pwd)/user:/octobot/user -v $(pwd)/tentacles:/octobot/tentacles -v $(pwd)/logs:/octobot/logs drakkarsoftware/octobot:stable
```

Running with docker-compose
---------------------------

A simple way to run a docker image is to use docker-compose :

-   Install [docker-compose](https://docs.docker.com/compose/install/)
-   Download the [docker-compose.yml
    file](https://github.com/Drakkar-Software/OctoBot/blob/master/docker-compose.yml)
-   Create a [.env]{.title-ref} file in the current folder
-   Add [HOST=YOUR\_IP\_ADDRESS]{.title-ref} in the newly created
    [.env]{.title-ref} file. (where YOUR\_IP\_ADDRESS is the ip address
    of the computer, can be replaced by [localhost]{.title-ref} if it's
    a local computer)
-   Start OctoBot with docker-compose (with the previous file
    [docker-compose.yml]{.title-ref} in the current folder) :

    ``` bash
    docker-compose up -d
    ```

You can now open the OctoBot web interface at <https://YOUR_IP_ADDRESS>.

Start multiple OctoBots with docker
-----------------------------------

To run a second OctoBot on the same computer :

1.  Create a new directory and enter it
2.  Start OctoBot's web interface on a new port by changing \"-p\"
    option

``` bash
docker run -itd --name OctoBot -p 8000:5001 -v $(pwd)/user:/octobot/user -v $(pwd)/tentacles:/octobot/tentacles -v $(pwd)/logs:/octobot/logs drakkarsoftware/octobot:stable
```

In this example, the second OctoBot's web interface is accessible at
<http://127.0.0.1:8000>.

Any port can be used except those already used by another OctoBot or any
software on your system.

Start OctoBot with docker managed files
---------------------------------------

{% hint style="warning" %}
It's easier to use but it will not be possible to update it without
deleting its files.
{% endhint %}

-v arguments can be removed from previous start commands but OctoBot's
local files will then be managed by docker (and not directly visible).

``` bash
docker run -itd --name OctoBot -p 80:5001 drakkarsoftware/octobot:stable
```

Local OctoBot files path are located in /var/lib/docker and can be
listed with the following command

``` bash
docker inspect -f '{{ .Mounts }}' OctoBot
```

To copy files of a directory outside the OctoBot container, for example
for logs files :

``` bash
docker cp OctoBot:/octobot/logs/. .
```

Wherer \"OctoBot\" is your container name
