Using a webhook with OctoBot
============================

There are many ways to wake your OctoBot up and make it do something,
one of them is using a webhook. With a webhook, you can automatically
send messages to your OctoBot from any website supporting this system.
<https://www.tradingview.com> is one of them.

In order to be able to receive the webhook's message, there are 2 possibilites:
1. On Cloud OctoBots, webhooks included and directly available. There is no need for extra configuration, you can jmup to step 3. of *Setting up your OctoBot's webhook*.
2. On self hosted OctoBots, use <https://ngrok.com/> to
act as a secure intermediary between the internet and your OctoBot.

Setting up your OctoBot's webhook
----------------------------------

1.  In OctoBot configuration, add the webhook service.
2.  To set up your webhook configuration

    * Option 1: If your OctoBot is not exposed to the Internet you have to :
      -   enable ngrok
      -   create an account on <https://ngrok.com/>
      -   copy your ngrok token from <https://dashboard.ngrok.com/get-started/your-authtoken>
      -   enter your ngrok token into your OctoBot's webhook service configuration.

    -   Option 2: If your OctoBot is exposed to the Internet you can
        disable ngrok and set the listening port and ip for the webhook.

    {% hint style="info" %}
    When using option 2 with docker you also need to add `-p 9000:9000` after `docker run`.
    {% endhint %}

3.  **Start here on Cloud OctoBots** Activate a tentacle using a webhook service (like the trading view
    signals trading mode).
4.  Restart your OctoBot.
5.  The webhook address will be displayed on your OctoBot configuration
    and printed in your logs.

    [![webhook and tradingview config](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/webhook_config.jpg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/webhook_config.jpg)

    [![webhook log](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/webhook_log.jpg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/webhook_log.jpg)

About ngrok.com
---------------

You can use ngrok with a free account, the only drawback of having a
free version is that your webhook address will change at every OctoBot
restart, you will have to update it on your message sender (like
<https://www.tradingview.com>)
