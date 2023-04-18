TradingView webhook
===================

With OctoBot, you can listen to <https://www.tradingview.com> signals
and automate trades.

OctoBot configuration
---------------------

Simply add the Trading-view service into your OctoBot's configuration
and setup your [webhook service](../Webhooks/Using-a-webhook-with-OctoBot.md).

TradingView account
-------------------

-   Create an account at <https://www.tradingview.com> (join for free
    button)
-   To be able to send signals from tradingview.com, you need a pro
    account, if you don't have one, you can use the pro trial by
    clicking on

    [![start-free-trial-button](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-go-pro-trial-button.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-go-pro-trial-button.png)

-   Add your credit card or paypal account to validate your trial
    account and click on

    [![start-trial-button](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-start-trial-button.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-start-trial-button.png)

Your account is now ready to be used with OctoBot !

Create an alert
---------------

-   Go to the right menu and click on the alert button

    [![alert-menu-button](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-alert-menu.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-alert-menu.png)

-   Create a new alert with

    [![create-alert-button](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-add-alert-button.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-add-alert-button.png)

-   Choose the condition : an indicator cross, a price drop, whatever
    you want
-   Add your OctoBot webhook as the following screenshot.

    [![set-webhook-url](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-alert-webhook-url.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-alert-webhook-url.png)

    You can find OctoBot's webhook on your OctoBot's configuration
    page or in OctoBot's starting logs. It should be an url like <https://XXXXXXXX.octobot.cloud/webhook/trading_view> or <http://XXXXXXXX.ngrok.io/webhook/trading_view>.

    WARNING: To improve performances, webhooks are started only when
    required, this means that **you need to activate a webhook related
    tentacle to get the webhook url** (a tentacle such as the **trading
    view signals trading mode**)

    [![webhook and tradingview config](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/webhook_config.jpg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/webhook_config.jpg)

    [![webhook log](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/webhook_log.jpg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/webhook_log.jpg)

-   Set the alert message

Alert format
------------

The alert format is designed to be easily used from TradingView. Minimal alerts contain the exchange name, the alert symbol (BTCUSDT for BTC/USDT and BTC/USDT:USDT) and the side of the order to create.
Example: 

``` bash
EXCHANGE={{exchange}}
SYMBOL={{ticker}}
SIGNAL=SELL
```

if it's a buy signal

OR

``` bash
EXCHANGE={{exchange}}
SYMBOL={{ticker}}
SIGNAL=SELL
```

if it's a sell signal

Additional order details can be added to the alert. These are optional:

``` bash
ORDER_TYPE=LIMIT
VOLUME=0.01
PRICE=42000
STOP_PRICE=38000
TAKE_PROFIT_PRICE=55000
REDUCE_ONLY=true
```

- `ORDER_TYPE` is the type of order, it can be `MARKET` or `LIMIT`
- `VOLUME`  is the volume of the order in base asset (BTC for BTC/USDT) it can a flat amount (ex: 0.1 to trade 0.1 BTC on BTC/USD), a % of the total portfolio value (ex: 2%) or a % of the available holdings (ex: 12a%). 
- `PRICE` is the price of the limit order in quote asset (USDT for BTC/USDT)
- `STOP_PRICE` is the price of the stop order to create. When increasing the position or buying in spot trading, the stop loss will automatically be created once the initial order is filled. When decreasing the position (or selling in spot) using a LIMIT `ORDER_TYPE`, the stop loss will be created instantly.
- `TAKE_PROFIT_PRICE` is the price of the take profit order to create. When increasing the position or buying in spot trading, the take profit will automatically be created once the initial order is filled. When decreasing the position (or selling in spot) using a LIMIT `ORDER_TYPE`, the take profit will be created instantly.
- `REDUCE_ONLY` when true, only reduce the current position (avoid accidental short position opening when reducing a long position). **Only used in futures trading**. Default is false

Example alert:

``` bash
EXCHANGE=binance
SYMBOL=ETHBTC
SIGNAL=SELL
ORDER_TYPE=LIMIT
```

[![alert-message](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-alert-message.png)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/tradingview-alert-message.png)

You can also use a token to add a security layer on your webhook using
an identification token, this token is randomly generated by your
OctoBot and can be found on the configuration interface and in execution
logs.

To add your token on the tradingview.com signal: add the following line
to the alert message:

``` bash
TOKEN=YOUR_TOKEN
```
