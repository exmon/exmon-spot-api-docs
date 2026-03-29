# Filters

Filters define trading rules for currency pairs and order execution in the EXMON Spot API.

All filters are derived from the `/pair_settings` endpoint and order parameters.

---

## Symbol Filters

### PRICE LIMITS

Defines allowed price range for a trading pair.

- `min_price` — minimum allowed price
- `max_price` — maximum allowed price

**Rules:**
- `price` >= `min_price`
- `price` <= `max_price`

**Example:**
```
{
  "min_price": "1",
  "max_price": "100000"
}
```
---

### QUANTITY LIMITS

Defines allowed quantity range.

- `min_quantity` — minimum order quantity
- `max_quantity` — maximum order quantity

**Rules:**
- `quantity` >= `min_quantity`
- `quantity` <= `max_quantity`

**Example:**
<pre>
{
  "min_quantity": "0.00001",
  "max_quantity": "1000"
}
</pre>
---

### AMOUNT LIMITS (Market Orders Only)

Defines limits for total order value (quote currency).

- `min_amount` — minimum total amount
- `max_amount` — maximum total amount

⚠ Applies only to market orders (`market_buy_total`, `market_sell_total`)

**Rules:**
- `amount` >= `min_amount`
- `amount` <= `max_amount`

**Example:**
<pre>
{
  "min_amount": "1",
  "max_amount": "50000"
}
</pre>

---

### PRICE PRECISION

Defines number of decimal places allowed in price.

- `price_precision`

**Rule:**
- Price must match allowed precision

**Example:**
<pre>
{
  "price_precision": 2
}
</pre>

---

### COMMISSION

Defines trading fees.

- `commission_maker_percent` — "0"
- `commission_taker_percent` — "0"

**Example:**
<pre>
{
  "commission_maker_percent": "0",
  "commission_taker_percent": "0"
}
</pre>

---

## Order Execution Filters

### EXECUTION TYPE (exec_type)

Applies to limit orders only.

- `post_only` — order will not execute immediately
- `fok` — fill-or-kill (must fully fill immediately or cancel)
- `ioc` — immediate-or-cancel (partial fill allowed, remainder canceled)

---

## Stop Market Filters

Used in `/stop_market_order_create`.

- `trigger_price` — activation price
- `quantity` — order size

**Rules:**
- `trigger_price` must respect pair price limits
- `quantity` must respect quantity limits

---

## Notes

- All filters are pair-specific via `/pair_settings`
- No global exchange-level filters exist
- No asset-level filters exist
- Market and limit orders have different validation rules
