OctoBot configuration is located in the **user** folder:

-   **user/config.json** is the global configuration file, mostly used
    to setup the bot exchanges credentials, interfaces and notification
    settings.
-   **user/profiles/** contains all the [profiles](Profiles.md)
    created and imported in your OctoBot.

OctoBot's web interface allows to easily edit the configuration,
however, it is also possible to manually edit configuration files.
Please be careful when manually editing them or OctoBot won't be able
to read them and wont start. Json file are readable and editable using
any text editor.

``` bash
ERROR    root <class 'Exception'>: Error when load config
```

This will appear when a configuration file is not a json valid file.

Profile configuration
=====================

**user/config.json** is the technical configuration file of OctoBot, an
example is available [on
github](https://github.com/Drakkar-Software/OctoBot/blob/master/octobot/config/default_config.json).

When starting OctoBot, if the **user** folder is missing or incomplete,
it will automatically be created or completed with default values.

Strategies
----------

Default profiles can't be edited, you can duplicate them to be able to
customize them. On default profiles strategy and trading mode
description are displayed instead of selectors to customize the profile.

[![profile_strategies](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/profile_strategies.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/profile_strategies.png)

When the configured profile is a custom profile, it can be configured,
[see custom profile page](Custom-Profile.md)

### Specific evaluator configuration

Some evaluators and trading modes can be configured.

If it is the case, configuration is possible through OctoBot's web
interface.

[![evaluators_config](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/specific_eval_config.jpg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/specific_eval_config.jpg)

This edition interface is generated according to the user inputs of the evaluator or trading mode to configure. Details in [the tentacles configuration docs](https://developer.octobot.info/tentacles/tentacle-package-development#configuration).

It is also possible to manually edit each configuration file using a
text editor for JSON. When configurable, each evaluator or trading mode
has a **NameOfTheRelatedClass.json** file in
**user/profiles/<profile_name>/specific_config**. Note: this file created in your profile after any change in the default configuration of the tentacle.

Currencies
----------

[![currencies](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/profile_currencies.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/profile_currencies.png)

OctoBot will trade all the cryptocurrencies listed in its configuration.
To tell which cryptocurrencies to trade, add the currency in the
**crypto-currencies** section in
**user/profiles/<profile_name>/profile.json**.

In order to keep OctoBot working at its full potential, we recommend to
trade **between 1 and 5** different assets **not to use more than 10 to
15** different assets at the same time, depending on the size of your
available funds.

### Wildcard

To tell OctoBot to trade all BTC trading pairs (with BTC as a quote
asset), use the wildcard "*" instead of a list for "pairs", directly in your profile's profile.json file:

``` json
"crypto-currencies":{
    "Bitcoin": {
      "pairs": ["*"],
      "quote": "BTC"
    }
}
```

A "quote" is required to specify the name of the currency to trade
with.

Exchanges
---------

[![exchanges](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/profile_exchanges.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/profile_exchanges.png)

For each profile, you can enable the exchanges you want to trade on.

It is also where you can select if you want to use **spot** or **future** trading on those exchanges.


Trading
-------

[![trading](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/profile_trading.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/profile_trading.png)

OctoBot can process two types of trading:

-   Real trading using your exchanges' portfolio.
-   Simulated trading using any imaginary portfolio.

### Reference-market

The **Reference-market** parameter defines which currency OctBot should
use as a reference, this reference is used to compute profitability and
the portfolio total value

### Risk

Any type of trading has its risk parameter. It is a parameter defining
the behavior of the trader, similarly to a real human trader.

The **Risk** parameter defines the behaviour of OctoBot in an optimism
manner.

It is a value between 0 and 1:

-   A low risk (closer to 0) will make OctoBot a very safe trader with
    few bold moves and mostly small trades. A 0 risk bot is very
    pessimistic (regarding its orders creation) and does not expect big
    market moves.
-   A high risk (closer to 1) will make OctoBot a very active and heavy
    trader. A 1 risk bot is very optimistic (regarding its orders
    creation) and is expecting significant market moves.

### Trader

When the **Enabled** parameter of the **Trader** section is set at **true**, OctoBot will trade
using your real funds from your exchange's accounts. When **false**
OctoBot will never any create a real trade.

### Load trade history

When the **load-trade-history** parameter is set at **true**, OctoBot
will load the account's recent trades for the enabled traded pairs at
startup. This allows to have a view on your account's trade history.
When **false**, OctoBot will only historize trades that happen after the
bot startup.

### Trader simulator

Additionally to the real trading system, a trading simulator is
available in OctoBot.

[Here is the article describing the simulator feature of
OctoBot](../Usage/Simulator.md)
