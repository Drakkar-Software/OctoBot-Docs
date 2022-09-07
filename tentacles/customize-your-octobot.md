# OctoBot is customizable!

## OctoBot is customizable !
You can easily create or add existing tentacles to your OctoBot.

Tentacles are evaluators \(using social media, trend analysis, news, ...\), strategies \(interpretations of evaluator's evaluations\), analysis tools \(implementation of a bollinger bands in depth analysis, twitter posts reader, ...\) and trading modes.

[![tentacles](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tentacles.jpg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tentacles.jpg)

OctoBot is available for free with [basic implementations of a lot of different evaluators](https://github.com/Drakkar-Software/OctoBot-Tentacles). The very high modularity in OctoBot's architecture allows it to automatically look for the most advanced version\(s\) of all the available tentacles and automatically use them in its trading strategies.

Therefore, anyone can implement its own version of any evaluator, strategy, analysis tool and trading modes. It's even possible to use another version provided by someone else !

# Tentacle installation

## Default tentacles

OctoBot default tentacles are automatically installed when first starting your OctoBot.

You can re-install them anytime using the following command arguments with your OctoBot: `tentacles --install --all`

It is also possible to install a tentacles package using the web interface Tentacles tab.

## Installing tentacles

To install tentacles, OctoBot can either install a tentacle package bundle or a single tentacle from a local folder.

### Creating a tentacle package bundle
Tentacle package bundles are the prefered way to share tentacles.

Steps to create a tentacles package bundle from a local folder:

1. Make sure it follows the [OctoBot-Tentacles folders architecture](https://github.com/Drakkar-Software/OctoBot-Tentacles) to properly locate tentacles to be installed. There is no need to create empty folders but packages with content have to be at the [appropriate path](tentacle-package-development.md#the-tentacle-package-folder).\
   Example: a trading mode should be located at **Trading/Mode/name\_of\_your\_trading\_mode** in your bundle.
2. Call OctoBot with the following arguments:

```bash
tentacles --pack "../tentacles_export.zip" --directory "path/to/your/local/tentacle_bundle"
```

{% hint style="info" %}
You now have a **tentacles_export.zip** file. It is a tentacle bundle containing your tentacles packages that you can install and share.
{% endhint %}

### Installing the tentacle package bundle

To install a package bundle, call OctoBot with the following arguments:

```bash
tentacles --install --all --location "path/to/your/tentacles_export.zip"
```

You can also make it available from an URL and later install it via (for example) :

```bash
tentacles --install --all --location "https://my.tentacles.com/pack_name"
```

{% hint style="info" %}
Installing a tentacle package will replace any existing source file that share the same name at the same path.
{% endhint %}

### Installing a single tentacle package

It is also possible to install a single tentacle package from a local folder using the following arguments:

```bash
tentacles --single-tentacle-install "path/to/your/tentacle/to/install" Evaluator/TA
```

Please note that in this command, you also need to provide the type of the tentacle (`Evaluator/TA` in this example).

### Installation troubleshoot

- **TentacleLoader       Error when loading _your_tentacle_module_** : This means the import of your tentacle module failed. Tentacles that can't be imported by Python can't be used.
- **Python doesn't even see my tentacle**: Your tentacle module has to be imported in your tentacle package `__init__.py` file. Your tentacle package has also to be imported in the parent folder `__init__.py`. Please note that this parent `__init__.py` file is managed by OctoBot and should already be properly filled when installing a tentacle bundle.
- **Python sees my tentacle but I can't see it on the web interface**: Your tentacle classes have to be listed in your **user/profiles/NameOfYourProfile/tentacles_config.json**. The web interface uses this file to list tentacles and check if they are enabled or not. This file is also kept up to date when installing a tentacle bundle.

In most cases, issues related to the **parent `__init__.py`** and `tentacles_config.json` files can be fixed by calling OctoBot with the following arguments:
```bash
tentacles --repair
```
