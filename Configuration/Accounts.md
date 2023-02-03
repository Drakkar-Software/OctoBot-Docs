Accounts
========

The accounts configuration page allows global (cross profile) configuration. It contains exchange API keys, interfaces credentials or keys and notification configuration.

Exchanges
---------

[![exchanges](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/accounts_exchanges.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/accounts_exchanges.png)

Once you have your own **user/config.json** file, to start using OctoBot with real money, you will just need to add your exchange credentials.

``` json
"exchanges": {
    "EXCHANGE_NAME": {
      "api-key": "",
      "api-secret": "",
      "enabled": false
    }
}
```

[Here is the doc helping to setup an exchange for OctoBot](Exchanges.md)

Interfaces
----------

[![interfaces](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/accounts_interfaces.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/accounts_interfaces.png)

Interfaces are all defined in **user/config.json** in the **services** section.

Here are different page explaining interfaces configuration :

-   [Web](../Interfaces/Web-interface.md)
-   [Discord](../Interfaces/Discord-interface.md)
-   [Reddit](../Interfaces/Reddit-interface.md)
-   [Telegram](../Interfaces/Telegram-interface.md)

Notifications
-------------

[![notifications](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/accounts_notifications.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/accounts_notifications.png)

When notifications are enabled, OctoBot will create notifications on all the given medias. These notifications contain the current evaluations of monitored markets as well as created, filled and cancelled orders.

Different types of notifications are available, it is possible to use any of them, or even all of them.

### Types of notifications

Alternatively to using the web interface to configure OctoBot notifications, you can edit your **user/config.json** file and edit this configuration:

``` json
"notification":{
  "global-info": true,
  "price-alerts": false,
  "trades": true,
  "notification-type": ["web"]
}
```

-   Set **global_info** to **true** to tell OctoBot to send general notifications like a startup message or a shutdown message.
-   Set **price_alerts** to **true** to tell OctoBot to send notifications when a price movement is detected and is triggering a new market state.
-   Set **trades** to **true** to tell OctoBot to send notifications when an order is created, filled or cancelled.

Add notifications types to **notification\_type** to tell which type of notification OctoBot should use. It is possible to have more than one type at the same time, in this case add a "**,**" between types. Example:

``` json
"notification-type": ["telegram", "web"]
```

Discord notifications use the Discord service. [See Discord service configuration docs](../Interfaces/Discord-interface.md)

### On Telegram

Open your **user/config.json** file and set the notification type value **telegram** :

``` json
"notification-type": ["telegram"]
```

Telegram notifications use the Telegram service. [See Telegram service configuration docs](../Interfaces/Telegram-interface.md)

### On Web Interface

Open your **user/config.json** file and set the notification type value **web**:

``` json
"notification-type": ["web"]
```

Web notifications use the Web service. [See Web service configuration docs](../Interfaces/Web-interface.md)
