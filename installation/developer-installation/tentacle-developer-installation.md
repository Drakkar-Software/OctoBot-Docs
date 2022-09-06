# Tentacle developer installation

## Requirements

* Python 3.8 ([download](https://www.python.org/downloads/))
* Git ([Download](https://git-scm.com/downloads))

## Instructions

{% hint style="info" %}
on **Windows Python3.8 has to be in environment variable** :

During [python install](https://www.python.org/downloads) **check** _add to environment var_ checkbox.
{% endhint %}

Open a command line and type :

```bash
git clone https://github.com/Drakkar-Software/OctoBot -b dev
cd OctoBot
python -m pip install -Ur requirements.txt
python start.py tentacles --install --all
```

{% hint style="info" %}
**python** is referring to your **Python3.8.X** installation, just adapt the commands to match your setup if any different (might be **python**, **python3**, **python3.8**, etc: it depends on your environment).

Note that python3.8 might be available under the name **python3.8** after this installation.
{% endhint %}

## Update OctoBot

### Requirements

**Python3.8.X**, **git** and an installed and **functional OctoBot setup** cloned from \[OctoBot github repository [https://github.com/Drakkar-Software/OctoBot](https://github.com/Drakkar-Software/OctoBot)]

```bash
git pull origin dev
python -m pip install -Ur requirements.txt
python start.py tentacles --install --all
```

{% hint style="info" %}
**python** is refering to your **Python3.8.X** installation, just adapt the commands to match your setup if any different (might be **python**, **python3**, **python3.8**, etc: it depends on your environment).
{% endhint %}
