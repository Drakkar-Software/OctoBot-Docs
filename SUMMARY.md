# Table of contents

* [Getting Started](README.md)
* [Users documentation](https://docs.octobot.online)

## Installation

* [Developer installation](installation/for-developers.md)

## Guides

* [OctoBot is customizable !](guides/customize-your-octobot.md)
* [Developer startup guide](guides/developer-guide.md)
* [Contribution](guides/contribution.md)

## Coding

* [Developer tips](coding/developers-tips.md)
* [Tests](coding/tests.md)

## Tentacles <a href="coding-1" id="coding-1"></a>

* [Tentacle package development](coding/tentacle-package-development.md)
* [Tentacle development](coding/tentacle-development.md)

## Scripted Trading

* [its python](scripted-trading/its-python.md)
* [Code editor](scripted-trading/code-editor.md)
* [common examples](scripted-trading/common-examples.md)

## scripted trading

* [built in variables](scripted-trading-1/built-in-variables/README.md)
  * [Page 1](scripted-trading-1/built-in-variables/page-1.md)
* [built in data](scripted-trading-1/built-in-data/README.md)
  * [exchange private data](scripted-trading-1/built-in-data/exchange-private-data.md)
  * [backtesting data](scripted-trading-1/built-in-data/backtesting-data/README.md)
    * [backtesting results](scripted-trading-1/built-in-data/backtesting-data/backtesting-results.md)
    * [trades](scripted-trading-1/built-in-data/backtesting-data/trades.md)
  * [Candle data](scripted-trading-1/built-in-data/candle-data/README.md)
    * [Time](scripted-trading-1/built-in-data/candle-data/time.md)
    * [Open](scripted-trading-1/built-in-data/candle-data/open.md)
    * [High](scripted-trading-1/built-in-data/candle-data/high.md)
    * [Low](scripted-trading-1/built-in-data/candle-data/low.md)
    * [Close](scripted-trading-1/built-in-data/candle-data/close.md)
    * [Volume](scripted-trading-1/built-in-data/candle-data/volume.md)
  * [trade history](scripted-trading-1/built-in-data/trade-history.md)
* [read/write any data](scripted-trading-1/read-write-any-data.md)
* [built in functions](scripted-trading-1/built-in-functions/README.md)
  * [Context](scripted-trading-1/built-in-functions/context.md)
  * [UI](scripted-trading-1/built-in-functions/ui/README.md)
    * [inputs](scripted-trading-1/built-in-functions/ui/inputs.md)
    * [Plotting](scripted-trading-1/built-in-functions/ui/plotting.md)
  * [TA](scripted-trading-1/built-in-functions/ta/README.md)
    * [third party TA libraries](scripted-trading-1/built-in-functions/ta/third-party-ta-libraries.md)
    * [since](scripted-trading-1/built-in-functions/ta/since/README.md)
      * [price since](scripted-trading-1/built-in-functions/ta/since/price-since.md)
      * [bars since](scripted-trading-1/built-in-functions/ta/since/bars-since.md)
      * [time since](scripted-trading-1/built-in-functions/ta/since/time-since.md)
    * [trigger](scripted-trading-1/built-in-functions/ta/trigger/README.md)
      * [tag triggered](scripted-trading-1/built-in-functions/ta/trigger/tag-triggered.md)
      * [evaluator triggered](scripted-trading-1/built-in-functions/ta/trigger/evaluator-triggered.md)
    * [wait for](scripted-trading-1/built-in-functions/ta/wait-for/README.md)
      * [wait for price](scripted-trading-1/built-in-functions/ta/wait-for/wait-for-price.md)
      * [wait for time](scripted-trading-1/built-in-functions/ta/wait-for/wait-for-time.md)
    * [durations](scripted-trading-1/built-in-functions/ta/durations/README.md)
      * [price duration](scripted-trading-1/built-in-functions/ta/durations/price-duration.md)
      * [time duration](scripted-trading-1/built-in-functions/ta/durations/time-duration.md)
  * [database writer](scripted-trading-1/built-in-functions/database-writer.md)
  * [database reader](scripted-trading-1/built-in-functions/database-reader.md)
  * [orders](scripted-trading-1/built-in-functions/orders/README.md)
    * [order types](scripted-trading-1/built-in-functions/orders/order-types/README.md)
      * [market](scripted-trading-1/built-in-functions/orders/order-types/market.md)
      * [limit](scripted-trading-1/built-in-functions/orders/order-types/limit.md)
      * [stop loss](scripted-trading-1/built-in-functions/orders/order-types/stop-loss.md)
      * [trailling market](scripted-trading-1/built-in-functions/orders/order-types/trailling-market.md)
      * [trailling stop loss](scripted-trading-1/built-in-functions/orders/order-types/trailling-stop-loss.md)
      * [trailling limit](scripted-trading-1/built-in-functions/orders/order-types/trailling-limit.md)
    * [order parameter](scripted-trading-1/built-in-functions/orders/order-parameter/README.md)
      * [traded pair](scripted-trading-1/built-in-functions/orders/order-parameter/traded-pair.md)
      * [side](scripted-trading-1/built-in-functions/orders/order-parameter/side.md)
      * [trailling method](scripted-trading-1/built-in-functions/orders/order-parameter/trailling-method.md)
      * [time limit](scripted-trading-1/built-in-functions/orders/order-parameter/time-limit.md)
      * [slippage limit](scripted-trading-1/built-in-functions/orders/order-parameter/slippage-limit.md)
      * [reduce only](scripted-trading-1/built-in-functions/orders/order-parameter/reduce-only.md)
      * [post only](scripted-trading-1/built-in-functions/orders/order-parameter/post-only.md)
      * [order tags](scripted-trading-1/built-in-functions/orders/order-parameter/order-tags.md)
      * [offsets](scripted-trading-1/built-in-functions/orders/order-parameter/offsets/README.md)
        * [min and max offset](scripted-trading-1/built-in-functions/orders/order-parameter/offsets/min-and-max-offset.md)
        * [trigger offset](scripted-trading-1/built-in-functions/orders/order-parameter/offsets/trigger-offset.md)
        * [offset](scripted-trading-1/built-in-functions/orders/order-parameter/offsets/offset.md)
      * [position size](scripted-trading-1/built-in-functions/orders/order-parameter/position-size/README.md)
        * [amount](scripted-trading-1/built-in-functions/orders/order-parameter/position-size/amount.md)
        * [target position](scripted-trading-1/built-in-functions/orders/order-parameter/position-size/target-position.md)
    * [cancel orders](scripted-trading-1/built-in-functions/orders/cancel-orders.md)
