# Tentacle development

## About Tentacles

This page covers tentacle development.

A tentacle is part of a [tentacle package](tentacle-package-development.md) and defines a tool for OctoBot such as a way to analyse moving averages, listen to reddit or create grid-like orders.

OctoBot uses tentacles to handle:

* Price technical analysis \(moving averages, RSI, MACD, ...\)
* Social analysis \(Telegram, Reddit and Google\)
* Evaluator signals interpretations \(strategies\)
* Orders creation and followup \(trading modes\)
* User interfaces and notifications \(web, telegram\)
* Backtesting data files reading and writing \(.data\)
* Exchanges fixes \(to handle exchange specific behaviors\)

There is no limit to the things OctoBot can handle: everything that can be coded can be used by OctoBot through a tentacle. It is possible to create a new tentacle to add a new tool to OctoBot or to build on an existing one and improve it.

## Developing a new Tentacle

The most efficient way to create a new tentacle si to build on top of an existing one to add features to it. It is of course also possible to create a new completely new tentacle.


### Developing a tentacle based on another one

To create a tentacle improving an existing one, all you need to do is to use the existing tentacle folder as a template \(to create a [tentacle package](tentacle-package-development.md)\) and extend the existing tentacle you want to improve and re-implement the methods you want to change in the package's python file.

Examples:

**RedditForumEvaluator** is a simple Reddit evaluator available by default in `tentacles/Evaluator/Social/forum_evaluator/forum.py`. Let's say you want to implement **SuperRedditForumEvaluator** which is a better Reddit evaluator.

Create the `tentacles/Evaluator/Social/super_forum_evaluator/` [tentacle package](tentacle-package-development.md) based on `tentacles/Evaluator/Social/forum_evaluator` and start coding the the python file.

```python
import tentacles.Evaluator.Social as Socials

class SuperRedditForumEvaluator(Socials.RedditForumEvaluator):
    # _get_sentiment is the RedditForumEvaluator method taking an entry and
    # returning a number representing the "bullishness" of the entry.
    # to change this part only, just redefine this method here
    def _get_sentiment(self, entry):
        # your new content
       sentiment = 1
       # some advanced entry analysis to set sentiment value
       return sentiment
```

**SimpleStrategyEvaluator** is a strategy available by default in `tentacles/Evaluator/Strategies/mixed_strategies_evaluator/mixed_strategies.py`. Create the `tentacles/Evaluator/Social/super_simple_strategy_evaluator/` [tentacle package](tentacle-package-development.md) based on `tentacles/Evaluator/Strategies/mixed_strategies_evaluator` and start coding the the python file.

```python
import tentacles.Evaluator.Strategies as Strategies

class SuperSimpleStrategyEvaluator(SimpleStrategyEvaluator):

   # _trigger_evaluation is the methods called when OctoBot is
   # asking for a strategy evaluation
   async def matrix_callback(self,
                             matrix_id,
                             evaluator_name,
                             evaluator_type,
                             eval_note,
                             eval_note_type,
                             exchange_name,
                             cryptocurrency,
                             symbol,
                             time_frame):
       final_evaluation = 0
       # some advanced computations to set final_evaluation value

       # update self.eval_note to store the strategy result
       self.eval_note = final_evaluation
       # finally, call self.strategy_completed to notify that
       # trading modes should wake up after this update
       await self.strategy_completed(cryptocurrency, symbol)
```

