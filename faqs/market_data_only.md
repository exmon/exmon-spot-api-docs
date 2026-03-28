# Market Data Only URLs

These endpoints provide public market data and do not require authentication.  
API keys are not required.

---

## REST API

Public market data is available via:

```
https://api.exmon.pro/v1.1
```

### Available endpoints

- `GET /ticker`
- `GET /trades`
- `GET /order_book`
- `GET /pair_settings`
- `GET /currency`
- `GET /currency_list_extended`
- `GET /candles_history`
- `GET /time`
- `GET /required_amount`

---

### Sample request

```bash
curl -sX GET "https://api.exmon.pro/v1.1/ticker?symbol=BTC_USDT"
```

---

## WebSocket Streams

Sample request:

```
wss://ws-api.exmon.pro:443/v1/trades
```

Full list of streams and formats is described in the WebSocket documentation.
