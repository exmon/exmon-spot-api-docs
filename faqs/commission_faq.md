# Commission Rates

## Disclaimer

- This document applies to EXMON Spot Exchange  
- Commission model may change in the future  
- Any changes will be reflected in API responses and changelog  

---

## What are Commission Rates?

Commission rates define the fee charged when an order is executed.

---

## Current Commission Model

EXMON Spot Exchange currently operates with **zero trading fees**.

### Active rates

- **maker:** 0.00000000  
- **taker:** 0.00000000  

No additional commissions apply:

- No tax commission  
- No special commission  
- No hidden fees  

---

## How do I check commission rates?

Commission rates can be retrieved via API.

### REST API

```bash
GET /api/v1/account/commission
```

### WebSocket API

```text
account.commission
```

### Example response

```json
{
  "symbol": "BTCUSDT",
  "commission": {
    "maker": "0.00000000",
    "taker": "0.00000000"
  }
}
```

---

## How is commission calculated?

Since all commission rates are zero:

```text
Commission = 0
```

This applies to:

- Market orders  
- Limit orders  
- Maker orders  
- Taker orders  

---

## Are there any exceptions?

No.  
All Spot trades execute with zero commission.

---

## Future Changes

EXMON may introduce commission models in the future, including:

- Maker / taker differentiation  
- Promotional discounts  
- Asset-based fee reductions  

All changes will be announced and reflected in API responses.
