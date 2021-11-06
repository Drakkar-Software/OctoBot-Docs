# offset



Example: limit(position=0, offset=e1%)

Example: traillingmarket(position=0, minoffset=5, maxoffset=5)

\


there is offset, minOffset and maxOffset, same values work on all.

* Offset makes it a static conditional order - a positive value means above the price and negative below
* minOffset and maxOffset makes it a trailling order. If the price changes such that the order becomes more than maxOffset away from the price, then the order will be moved to minOffset away again.

\


For an asset quoted in USD (eg BTCUSD), offset can be given in the following ways:

* offset=50    $50 from the current price.
* offset=1%    offset is calculated as a percentage of the current price. If the price is $10,000, and offset is 1%, then 1% of 10,000 is 100. A Offset of $100 will be used.
* offset=@950    The @ at the start of the value indicates this should be treated as an absolute price of $950, regardless of what the current price is. The difference between the current price and this absolute price is then calculated, and the trailling order will maintain this distance from the live price.
* offset=e50    With an open position, offset will be relative to average entry. With no open position and on spot, offset will be relative to current price
* offset=e1%    With an open position, offset will be relative to average entry. With no open position and on spot, offset will be relative to current price
