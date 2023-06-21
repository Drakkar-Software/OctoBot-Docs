Accounts
========

The accounts configuration page allows global (cross profile) configuration. It contains exchange API keys, interfaces credentials or keys and notification configuration.

Exchanges
---------

[![exchanges](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/accounts_exchanges.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/accounts_exchanges.png)

You can save as many accounts as you want and only trade on those enabled in your profile. 

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

-   **Global-Info**: General notifications like a startup message or a shutdown message.
-   **Price-Alerts**: A price movement is detected and is triggering a new market state.
-   **Trades**: An order is created, filled or cancelled.
-   **Trading-Script-Alerts**: Any notification related to a scripted trading mode.
-   **Other**: Other type of notifications.

Enable notifications types to tell which types of notifications OctoBot should use.

### Telegram notifications

When selected, notifications will be sent to you on Telegram.

Telegram notifications use the Telegram service. [See Telegram service configuration docs](../Interfaces/Telegram-interface.md)

### Web notifications

When selected, notifications will be sent to you on the web interface.

Web notifications use the Web service. [See Web service configuration docs](../Interfaces/Web-interface.md)
