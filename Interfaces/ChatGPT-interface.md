ChatGPT interface
=================

OctoBot uses the ChatGPT interface to interact with ChatGPT.

Ths interface is pre-configured on [Cloud OctoBots](https://www.octobot.cloud/) and has to be configured in self hosted OctoBot

ChatGPT service configuration
-----------------------------

{% hint style="info" %}
No configuration is needed for [Pro Cloud OctoBots](https://www.octobot.cloud/).
{% endhint %}

To use ChatGPT, the only configuration you need is to enter your OpenAI API key into the GPT Interface

1. Create or login to your [openai](https://platform.openai.com/) account
2. Create a new API key on https://platform.openai.com/account/api-keys
3. Copy your API key into the GPT configuration in the Accounts tab of the web interface

![gpt config](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/gpt_config.png)

Costs 
-----

{% hint style="info" %}
When using [Pro Cloud OctoBots](https://www.octobot.cloud/), we are covering the GPT calls cost.
{% endhint %}

Using ChatGPT from automated API calls is a paid service from OpenAI. Each call to ChatGPT will consume a few OpenAI tokens.

Each call to ChatGPT is recrating a request which usually consumes around 90 OpenAI tokens.
You can get the current price of OpenAI token from [this page](https://openai.com/pricing).

You can estimate the cost of using ChatGPT related features by estimating the amount of requests per day.

{% hint style="info" %}
Running a strategy on 4h for 2 trading pairs on 1 exchange: the GPT evaluator will be called every 4 hours for each trading pair for each exchange.
{% endhint %}
