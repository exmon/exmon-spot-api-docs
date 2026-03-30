# SPOT API Glossary

**Disclaimer:** This glossary applies only to the EXMON SPOT API. Definitions may differ for Futures, Options, or other systems.

---

### A

`ACK`
* `newOrderRespType` enum. Response type where only basic fields are returned: `symbol`, `order_id`, `client_id`, `created_at`.

`aggTrade` / Aggregate trade
* Aggregation of one or more trades executed at the same price within a short time window.

`askPrice`
* Lowest price on the `SELL` side of the order book.

`askQty`
* Quantity available at the lowest `SELL` price.

`asks`
* All sell orders in the order book.

`avgPrice`
* Volume-weighted average price over a defined interval.

---

### B

`baseAsset`
* First asset in the pair (e.g. BTC in BTC_USDT). Represents the asset being traded (quantity).

`baseAssetPrecision`
* Number of decimals allowed for the base asset.

`bidPrice`
* Highest price on the `BUY` side.

`bidQty`
* Quantity available at the highest `BUY` price.

`bids`
* All buy orders in the order book.

`BUY`
* Order side indicating purchase of the base asset.

---

### C

`CANCELED`
* Order status indicating the order was canceled by the user.

`client_id`
* User-defined identifier for an order.

`commission`
* Fee paid for a trade.

`commission_asset`
* Asset used to pay commission.

`cumulative_quote_qty`
* Total value of executed trades (`price * qty` summed across fills).

---

### D

Data Source
* Indicates where the data is retrieved from (engine, memory, database).

---

### E

`executed_qty`
* Total filled quantity of the order.

`EXPIRED`
* Order status indicating the remaining unfilled quantity was canceled by the system.

---

### F

`filters`
* Trading rules and limits applied to symbols.

`FOK` / Fill or Kill
* Order must be fully filled immediately or canceled.

`free`
* Available balance not locked in orders.

`FULL`
* Response type including full order details and fills.

---

### G

`GTC` / Good Till Canceled
* Order remains active until filled or manually canceled.

---

### I

`IOC` / Immediate or Cancel
* Order fills partially or fully immediately; remaining quantity is canceled.

---

### K

`kline`
* Candlestick data including open, high, low, close, and volume.

---

### L

`lastPrice`
* Price of the most recent trade.

`lastQty`
* Quantity of the most recent trade.

`LIMIT`
* Order type executed at a specified price or better.

`locked`
* Balance reserved in open orders.

---

### M

`MARKET`
* Order type that executes immediately against available liquidity.

Matching Engine
* Core system that processes orders and matches trades.

Memory
* Cached data source for faster API responses.

---

### N

`NEW`
* Order status indicating it was accepted by the system.

`newClientOrderId`
* Identifier provided when placing an order.

Notional value
* Total value of the order (`price * qty`).

---

### O

Order Book
* List of current bids and asks.

`order_id`
* Unique identifier of an order.

`orig_qty`
* Original order quantity.

`orig_client_id`
* Original client-provided order ID.

---

### P

`PARTIALLY_FILLED`
* Order status indicating partial execution.

---

### Q

`quantity`
* Amount of base asset to buy or sell.

`quoteAsset`
* Second asset in the pair (e.g. USDT in BTC_USDT).

`quoteOrderQty`
* Amount of quote asset used in reverse MARKET orders.

`quote_qty`
* Total value of trade (`price * qty`).

---

### R

`recvWindow`
* Time window (ms) during which request is valid.

`RESULT`
* Response type without fills.

Reverse `MARKET` order
* MARKET order defined using `quoteOrderQty`.

---

### S

`SELL`
* Order side indicating selling the base asset.

`SPOT`
* Trading type with immediate settlement.

`symbol`
* Trading pair (e.g. BTC_USDT).

---

### T

`ticker`
* Market summary data including price changes.

`time`
* Timestamp of trade or order.

`timeInForce`
* Order execution rule (`GTC`, `IOC`, `FOK`).

`TRADING`
* Symbol status allowing trading.

`transactTime`
* Timestamp of order execution/update.

---

### U

`updateTime`
* Last update timestamp of the order.

---

### W

`weightedAveragePrice`
* Volume-weighted average price over a time interval.
