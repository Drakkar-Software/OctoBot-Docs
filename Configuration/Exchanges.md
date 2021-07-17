Exchanges
=========

To know more about an exchange support in OctoBot, please have a look at [exchanges documentation](https://exchanges.docs.octobot.online).

Web interface configuration
---------------------------

Octobot reads trading data (prices, volumes, trades, etc) from
exchanges. At least one exchange is required for OctoBot to perform
trades. In [simulation mode](Simulator.html#simulator), exchange API
keys configuration is not necessary.

[![exchanges](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/exchanges.jpg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/exchanges.jpg)

You can configure OctoBot's exchanges using the [web
interface](Web-interface.html) **configuration** tab.

Manual configuration
--------------------

In **user/config.json**, find this lines:

``` json
"exchanges": {

}
```

Edit this lines and add the exchange(s) you want to use.

In OctoBot configuration, exchange connection info are encrypted. To
manually add exchange configuration, you can add your info directly into
your **user/config.json** file, OctoBot will then take care of the
encryption for you.

If you want to encrypt your exchange keys before starting OctoBot, you
can use the following instructions:

Start the OctoBot with option **--encrypter** like below :

``` bash
python start.py --encrypter
```

And copy and paste your api-key and api-secret to your configuration
file (see example below).

Example with Binance and Coinbase Pro :

``` json
"exchanges": {
    "binance": {
        "api-key": "YOUR_BINANCE_API_KEY_ENCRYPTED",
        "api-secret": "YOUR_BINANCE_API_SECRET_ENCRYPTED"
    },
    "coinbasepro": {
        "api-key": "YOUR_EXCHANGE_API_KEY_ENCRYPTED",
        "api-secret": "YOUR_EXCHANGE_API_SECRET_ENCRYPTED",
        "api-password": "YOUR_EXCHANGE_API_SECRET_ENCRYPTED"
    }
}
```

-   **api-key** is your exchange account API key
-   **api-secret** is your exchange account API secret
-   **api-password** is your exchange account API password if this
    exchange is requiring a password. Leave empty otherwise

Simulated exchange
------------------

To use the Simulated exchange feature of the Octobot, you have to
specifiy a [trader simulator](Simulator.html) configuration. To use an
exchange in simulation only, you also have to specify its configuration
as described above. For most exchanges, API credentials are not required
in simulation mode, adding the exchange with default values is enough.
