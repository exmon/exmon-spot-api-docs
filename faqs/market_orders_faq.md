# Order Execution & Behavior

## Key Behavior

### 1. Full Balance Required
If the user does not have enough balance to cover the order:
- Order is **REJECTED**

---

### 2. Partial Fill (Low Liquidity)
If there is not enough liquidity to fill the entire order:
- Order is **PARTIALLY_FILLED**
- Remaining amount is **automatically canceled**
- Final status: **EXPIRED**

---

### 3. Execution Logic (EXMON)
Unlike exchanges with persistent streams, EXMON operates via REST:
- Matching happens instantly.
- Trades are recorded immediately.
- Order status is final at the time of the API response.

---

## Order Status Flow

Possible status transitions:
- NEW → PARTIALLY_FILLED → FILLED
- NEW → PARTIALLY_FILLED → EXPIRED
- NEW → FILLED

---

## Example: Partial Fill Scenario
User places a request: **BUY 6 LTC at MARKET**

Order book liquidity available:
- 2 LTC @ 1.0
- 2 LTC @ 1.0
- (No more sellers available)

---

## API Response (EXMON-style)
```
{
    "symbol": "LTC_USDT",
    "order_id": 32,
    "client_id": "8LGC97RRgNPVQk979VIhjt",
    "type": "market",
    "side": "buy",
    "orig_qty": "6.00000000",
    "executed_qty": "4.00000000",
    "quote_spent": "4.00000000",
    "status": "EXPIRED",
    "created_at": 1719467634105,
    "fills": [
        {
            "price": "1.00000000",
            "qty": "2.00000000",
            "commission": "0.00000000",
            "commission_asset": "USDT",
            "trade_id": 7
        },
        {
            "price": "1.00000000",
            "qty": "2.00000000",
            "commission": "0.00000000",
            "commission_asset": "USDT",
            "trade_id": 8
        }
    ]
}
```
---

## Public Market Data (EXMON API)
Since the EXMON API is public-only, executed trades can be retrieved via the following endpoint:

**POST /trades**
``
https://api.exmon.pro/v1.1/trades
``

**Example Request:**
```
{
    "pair": "LTC_USDT",
    "limit": 50
}
```

**Example Response:**
```
[
    {
        "trade_id": 8,
        "price": "1.00000000",
        "amount": "2.00000000",
        "side": "buy",
        "timestamp": 1719467634105
    },
    {
        "trade_id": 7,
        "price": "1.00000000",
        "amount": "2.00000000",
        "side": "buy",
        "timestamp": 1719467634105
    }
]
```

---

## Important Notes

### No User Data Stream
EXMON does NOT provide:
- executionReport
- WebSocket order updates
- Real-time account events

All order tracking must be managed via:
- Internal systems
- Database logs
- Admin panel

### Commission Handling
- Commission is applied per fill.
- Commission asset depends on the specific pair configuration.
- Total commission is the sum of all individual fills (Current fee: 0%).

### Liquidity Edge Cases
- Empty Order Book: Order is REJECTED.
- Partial Fill: Remaining volume is NOT queued; it is canceled immediately with status EXPIRED.

---

## Summary
- MARKET orders consume liquidity instantly.
- No queuing, no waiting.
- Partial fill results in an EXPIRED remainder.
- Everything is final within a single API response.
- Public API displays executed trades only, not individual orders.
- EXMON = Simple execution model without hidden states.
