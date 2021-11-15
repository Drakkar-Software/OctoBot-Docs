# trigger offset



* #### Trigger Offsets

Example: market(position=100, triggeroffset=50)

\


Defines how far away from the price the order should get activated, a positive value is above and a negative below the price, offset can be given in the following ways:

* triggerOffset=50    trigger the order at $50 from the current price.
* triggerOffset=1%    trigger the order when the price moves 1% into profit.
* triggerOffset=@950    trigger the order when the price reach $950.
* triggerOffset=e50    With an open position, offset will be relative to average

entry. With no open position and spot, offset will be relative to current price

* triggerOffset=e1%    With an open position, offset will be relative to average

entry. With no open position and Spot, offset will be relative to current price
