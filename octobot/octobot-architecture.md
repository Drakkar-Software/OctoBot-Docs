# OctoBot architecture

{% hint style="info" %}
This page is referring to OctoBot in versions superior to 0.4.0.
{% endhint %}

### Philosophy

The goal behind OctoBot is to have a **very fast and scalable** trading robot.

To achieve this, OctoBot is entirely built around the [asyncio](https://docs.python.org/3/library/asyncio.html) producer-consumer [Async-Channel](https://github.com/Drakkar-Software/Async-Channel) framework which allows to very quickly and efficiently transmit data to different elements within the bot. The idea is all the time maintain **fully up-to-date data** without having to use update loops (that require have inefficient sleeping time) while also **waking up the evaluation chain as quickly as possible** when an update is available (without having to wait for any update cycle of any update loop).

Additionally, in order to save CPU time, as little threads as possible are use by OctoBot (usually less than 10 with a standard setup).

As a final touch, each CPU or memory intensive task is further optimized using [Cython](https://cython.org/). The python code of these tasks is translated into highly optimized C code that allows for less instructions to process and optimized memory representation ending up with a huge performance increase.

### Overview

The OctoBot code is split into [several repository](octobot-repositories.md). Each module is handled as an independent python module and is available on the [official python package repository](https://pypi.org/) (used in `pip` commands). Modules are made available as python source modules as well as as compiled modules which includes cython optimizations. Installing a module on a platform which as not already been built and made available on [pypi.org](https://pypi.org/) will take much more time as `pip` will cythonize and compile the given module, which also requires a cpp compiler.

### OctoBot

[![OctoBot architecture](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki\_resources/octobot\_arch.svg)](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki\_resources/octobot\_arch.svg)

Simplified view of the OctoBot core components.

{% hint style="info" %}
Inside the OctoBot part, each arrow is an async channel.
{% endhint %}

### OctoBot tentacles

Tentacles are OctoBot's extensions, they are meant to be easily customizable, can be activated or not and do any specific action within OctoBot.

#### Evaluation chain tentacles

They are tools to analyze market data as well as any other type of data (reddit, telegram, etc). They implement abstract evaluators, strategies and trading modes.

#### Utility tentacles

These are OctoBot's interfaces (web, telegram), notification systems, social news feeds and backtesting data collectors. They implement abstract interfaces, services, service feeds, notifiers and data collectors

### Evaluators, strategies and trading modes:

#### Evaluators

Simple python classes that will automatically be wake up when new data is available. Their goal is to set `self.eval_note` and call `await self.evaluation_completed` that will then be made available to the Strategy(ies). They should be dedicated to a single simple task such as (for example) evaluate the RSI on the current data or looks for a divergence in a trend.

#### Strategies

Strategies are more complex elements, they can read all the evaluators evaluations on every time frame and are considering these evaluations to set their `self.eval_note` and call `await self.strategy_completed`. As a comparison if evaluators are human senses, strategies are the brain that will take these senses' signals and decide to do something or not. Strategies can be generic like SimpleStrategyEvaluator that will take any standard evaluator and time frame into account or using specific evaluators only like MoveSignalsStrategyEvaluator.

#### Trading modes

Trading modes use the strategy(ies) evaluations to create, update or cancel orders. Using the strategies signals, they are responsible for the way to translate a signal into an order by looking at the available funds, open orders, considering stop loss or not and other trading related responsibilities.

#### Triggers

Evaluators, strategies and trading modes are automatically triggered when their channel has a new data. Trigger sources are:

For evaluators

* Technical evaluators: any new candle or refresh request (with updated candles data) from a strategy
* Real time evaluators: any new candle and any market price change
* Social evaluators: associated signal (ex: a post for a reddit social evaluator)

For strategies

*   After a technical evaluator cycle: when all TA have updated their

    evaluation and called `await self.evaluation_completed`
*   After any real time evaluator evaluation and call of

    `await self.evaluation_completed`
*   After any social evaluator evaluation and call of

    `await self.evaluation_completed`

For trading mode

*   After any strategy evaluation and call of

    `await self.strategy_completed`

_Thanks for reading this guide and if you have any idea on how to improve it, please reach out to us !_
