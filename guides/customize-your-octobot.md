# OctoBot is customizable !

You can easily create or add existing tentacles to your OctoBot.

Tentacles are evaluators \(using social media, trend analysis, news, ...\), strategies \(interpretations of evaluator's evaluations\), analysis tools \(implementation of a bollinger bands in depth analysis, twitter posts reader, ...\) and trading modes.

[![tentacles](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tentacles.jpg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tentacles.jpg)

OctoBot is available for free with [basic implementations of a lot of different evaluators](https://github.com/Drakkar-Software/OctoBot-Tentacles). The very high modularity in OctoBot's architecture allows it to automatically look for the most advanced version\(s\) of all the available tentacles and automatically use them in its trading strategies.

Therefore, anyone can implement its own version of any evaluator, strategy, analysis tool and trading modes. It's even possible to use another version provided by someone else !

# Tentacle installation

## Default tentacles

OctoBot default tentacles are automatically installed when first starting your OctoBot.

You can re-install them anytime using the following command arguments to your OctoBot: `tentacles --install --all`

It is also possible to install a tentacles package using the web interface Tentacles tab.

## Installing tentacles

To install tentacles, OctoBot can either install a tentacle package bundle or a single tentacle from a local folder.

### Creating a tentacle package bundle
Tentacle package bundles are the prefered way to share tentacles.

To create a tentacles package bundle from a local folder:

1. Make sure it follows the [OctoBot-Tentacles folders architecture](https://github.com/Drakkar-Software/OctoBot-Tentacles) to properly locate tentacles to be installed. There is no need to create empty folders but packages with content have to be at the [appropriate path](../coding/tentacle-package-development.md#the-tentacle-package-folder).  
Example: a trading mode should be located at **Trading/Mode/name_of_your_trading_mode** in your bundle.

2. Call OctoBot with the following arguments:

```bash
tentacles --pack "../tentacles_export.zip" --directory "path/to/your/local/tentacle_bundle"
```

{% hint style="info" %}
You now have a **tentacles_export.zip** file that is a tentacle bundle containing your tentacles packages that you can install and share.
{% endhint %}

### Installing the tentacle package bundle

To install a package bundle, use the following arguments:

```bash
tentacles --install --all --location "path/to/your/tentacles_export.zip"
```

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

