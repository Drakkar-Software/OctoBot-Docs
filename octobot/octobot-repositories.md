# OctoBot repositories

#### OctoBot repositories

OctoBot code is split into multiple repositories:

*   [https://github.com/Drakkar-Software/OctoBot](https://github.com/Drakkar-Software/OctoBot) (dev branch) for the
    main program initialization, backtesting and strategy optimizer setup as well as community data management.
*   [https://github.com/Drakkar-Software/OctoBot-Tentacles](https://github.com/Drakkar-Software/OctoBot-Tentacles) (dev branch)
    tentacles: evaluators, strategies, trading modes, interfaces, notifiers, external data feeds (twitter, telegram etc), backtesting data formats management and exchange specific behaviors.
*   [https://github.com/Drakkar-Software/OctoBot-Trading](https://github.com/Drakkar-Software/OctoBot-Trading) for everything
    trading and exchange related: exchange connections, exchange data
    fetch and update, orders, trades and portfolios management.
*   [https://github.com/Drakkar-Software/OctoBot-evaluators](https://github.com/Drakkar-Software/OctoBot-evaluators) for
    everything related to evaluators and strategies.
*   [https://github.com/Drakkar-Software/OctoBot-Services](https://github.com/Drakkar-Software/OctoBot-Services) for
    everything related to interfaces: graphic (web) and text(telegram), notifications push and social analysis data management: update engine to handle new data from an external feed (ex: twitter) when it gets available.
*   [https://github.com/Drakkar-Software/OctoBot-Backtesting](https://github.com/Drakkar-Software/OctoBot-Backtesting) for the
    backtesting engine and scheduling as well as historical data collection unified storage management.
*   [https://github.com/Drakkar-Software/OctoBot-Tentacles-Manager](https://github.com/Drakkar-Software/OctoBot-Tentacles-Manager) for
    tentacles installation, updates and interactions: get a tentacle documentation, configuration or it's dependencies.
*   [https://github.com/Drakkar-Software/OctoBot-Commons](https://github.com/Drakkar-Software/OctoBot-Commons) for common
    tools and constants used across each above repository.
*   [https://github.com/Drakkar-Software/Async-Channel](https://github.com/Drakkar-Software/Async-Channel) which is used by
    OctoBot as a base framework for every data transfer within the bot. This allows a highly optimized and scalable architecture that adapts to any system while using a very low amount of CPU and RAM.
