# Getting Started

## Officially supported exchanges

* [Binance](partners/binance/)
* [Coinbase Pro](officially_supported/coinbase_pro.md)
* [Kucoin](officially_supported/kucoin.md)
* [FTX](partners/ftx/)
* [Ascendex](partners/ascendex/)
* [OKEx](partners/okex/)
* [Okcoin](partners/okcoin/)
* [GateIO](partners/gateio/)
* [Huobi & Huobi Pro](partners/huobi/)

## Partner exchanges - Support OctoBot

As the OctoBot team, **our goal is to keep providing OctoBot for free**. However developing and maintaining the project comes at a cost. Therefore we rely on exchanges partnerships to propose the most convenient way to support OctoBot.

By using OctoBot on real trading with our partner exchanges, you contribute to support the project and it won't cost you any money.

If an account you are using is not meeting a partner exchange requirement, you will see an error message: this doesn't prevent your from using OctoBot. However the OctoBot team would greatly appreciate if you could create a new account that meets the exchange's requirements to support the project.

Here are the current partners:

* [Binance](partners/binance/)
* [Bybit](partners/bybit/)
* [FTX](partners/ftx/)
* [Ascendex](partners/ascendex/)
* [OKEx](partners/okex/)
* [Okcoin](partners/okcoin/)
* [GateIO](partners/gateio/)
* [Huobi & Huobi Pro](partners/huobi/)

## Community tested exchanges

* [Kraken](community_tested/kraken.md)
* [HitBTC](community_tested/hitbtc.md)
* [Bitfinex](community_tested/bitfinex.md)
* [Bittrex](community_tested/bittrex.md)
* [COSS](community_tested/coss.md)
* [Bitstamp](community_tested/bitstamp.md)
* [Poloniex](community_tested/poloniex.md)
* [Bithumb](community_tested/bithumb.md)
* [Upbit](community_tested/upbit.md)
* [Crex24](community_tested/crex24.md)
* [Wavesexchange](community_tested/wavesexchange.md)
* [Cryptopia](community_tested/cryptopia.md)

## Exchanges supported technologies

If you want use any exchange that is available [here](https://github.com/ccxt/ccxt/wiki/Exchange-Markets), the REST interface should work but **it's at your own risk** since we did not test it yet.

### REST

The REST technology is a HTTP polling based interface where exchanges have to be frequently requested to refresh OctoBot's databases.
It: 
* is **slower**: it might take a few seconds to update prices and orders 
* can handle a **limited** amount of requests per seconds due to exchanges restrictions. Therefore only a limited amount of trading pairs can be handled simultaneously when using a REST interface. 

### Websocket

The websocket technology allows for permanent channels between exchanges and OctoBot from which exchanges directly push updated information to OctoBot.
It:
* is **almost instantaneous**: updates are directly pushed to OctoBot when updated on the exchange 
* is **limitless** regarding the amount trading pairs that can be handled simultaneously
