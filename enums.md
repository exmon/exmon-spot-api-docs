# ENUM Definitions

This document describes all ENUM values used in the EXMON API (Public, Private, Voucher).

Only values explicitly present in request parameters or API responses are included.

---

## Trade Type (`type`)

Used in:
- `/trades`
- `/user_trades`
- `/order_trades`

* `buy`
* `sell`

---

## Order Type (`type`)

Used in:
- `/order_create`
- `/user_open_orders`
- `/user_cancelled_orders`

### Limit Orders

* `buy`
* `sell`

### Market Orders

* `market_buy`
* `market_sell`
* `market_buy_total`
* `market_sell_total`

### Stop Market Orders

* `stop_market_buy`
* `stop_market_sell`

---

## Execution Type (`exec_type`)

Used in:
- `/order_create` (request)
- `/user_trades` (response)
- `/order_trades` (response)

### Order creation (request)

* `post_only`
* `fok`
* `ioc`

### Trade execution (response)

* `maker`
* `taker`

---

## Payment Provider Type (`type`)

Used in:
- `/payments/providers/crypto/list`

* `deposit`
* `withdraw`

---

## Candle Resolution (`resolution`)

Used in:
- `/candles_history`

* `1`
* `5`
* `15`
* `30`
* `45`
* `60`
* `120`
* `180`
* `240`
* `D`
* `W`
* `M`

---

## Cancel Reason Status (`reason_status`)

Used in:
- `/user_cancelled_orders`

* `user_canceled`

---

## Notes

* All ENUM values are case-sensitive
* ENUM values are returned exactly as shown in API responses
* No additional ENUM types are defined beyond those listed above
