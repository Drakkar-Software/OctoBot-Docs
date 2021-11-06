# target position



Example:&#x20;

```
market(ctx, target_position=100)
```

An alternative way to calculate the side and amount for the order. When using position, the values for side and amount will be ignored, as they are calculated by the bot for you.

The amount traded will be the difference between the current open position and the given position size. For example, if your current position is 100 contracts long, and you request a target position of 300, then an order will be placed to buy 200 additional contracts (the difference between your current position and target position). In fact, regardless of your current position (long, short, nothing), the order will be whatever size it needs to be to ensure you finish with an open position of the target size.&#x20;

## &#x20;   Examples with 500$ open long position

```
position=1000        Buy 500 contracts, resulting in a position size of +1000
position=200        Sell 300 contracts, leaving you with +200.
position=0            Sell 500 contracts. This will effectively close your position, regardless of it's current size.
position=-500        Sell 1000 contracts, taking you from +500 contracts long to -500 contracts short.
position=50%p    Target position size will be 50% of your current position size
position=50%a    Same as 50%% - the a stands for Available Balance
```
