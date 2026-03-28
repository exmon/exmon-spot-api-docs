<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Public Rest API for EXMON](#public-rest-api-for-exmon)


<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Public Rest API for EXMON

## General API Information

* The following base endpoints are available. Please use whichever works best for your setup:
```
  https://api.exmon.pro
```

* Responses are in JSON by default.

* If your request contains a symbol name containing non-ASCII characters, then the response may contain non-ASCII characters encoded in UTF-8.

* Some endpoints may return asset and/or symbol names containing non-ASCII characters encoded in UTF-8 even if the request did not contain non-ASCII characters.

* Data is returned in chronological order, unless noted otherwise.
  * Without `startTime` or `endTime`, returns the most recent items up to the limit.
  * With `startTime`, returns oldest items from `startTime` up to the limit.
  * With `endTime`, returns most recent items up to `endTime` and the limit.
  * With both, behaves like `startTime` but does not exceed `endTime`.

* All time and timestamp related fields in the JSON responses are in milliseconds by default.

* Timestamp parameters (e.g. `startTime`, `endTime`, `timestamp`) can be passed in milliseconds or microseconds.

* For APIs that only send public market data, use the dedicated market data base endpoint if available.

* APIs have a timeout of 10 seconds when processing a request.

* If a response from backend takes longer than this, the API responds with timeout error.
This does not always mean that the request failed internally.

* If the status of the request has not appeared in user stream or query endpoints, please perform a status check request.

* Please avoid SQL keywords in requests as they may trigger security filtering rules.

---

## HTTP Return Codes

* HTTP 4XX return codes are used for malformed requests; the issue is on the sender's side.

* HTTP 403 return code is used when a WAF rule has been violated. This can indicate rate limit violation or security block.

* HTTP 409 return code is used when a cancel/replace order partially succeeds.

* HTTP 429 return code is used when breaking a request rate limit.

* HTTP 418 return code is used when an IP has been auto-banned after repeated rate limit violations.

* HTTP 5XX return codes are used for internal errors; the issue is on the server side.
* It is important not to treat this as a final failure as execution status may be unknown.

---

## Error Codes

Any endpoint can return an error.

Sample payload:
<pre>
{
  "code": -1000,
  "message": "Invalid request parameters"
}
</pre>
Specific error codes and messages are defined in the Error Codes section.

---

## General Information on Endpoints

* For GET endpoints, parameters must be sent as a query string.

* For POST, PUT, and DELETE endpoints, parameters may be sent either in query string or request body with
content type application/x-www-form-urlencoded.

* Parameters may be sent in any order.

* If a parameter is sent in both query string and request body, the query string parameter will be used.

---

## LIMITS

### General Info on Limits

* Interval letters:
  * SECOND => S
  * MINUTE => M
  * HOUR => H
  * DAY => D

* intervalNum describes the amount of interval.
* Example: intervalNum 5 with intervalLetter M means "Every 5 minutes".

* Requests exceeding rate limits return HTTP 429.

---

### IP Limits

* Each response includes X-USED-WEIGHT headers indicating current usage per IP.

* Each endpoint has a weight determining its cost.

* When 429 is received, you must back off requests.

* Repeated violations may result in temporary IP ban (HTTP 418).

* Retry-After header indicates wait time.

---

### Unfilled Order Count

Each successful order response includes order count headers.

If exceeded, HTTP 429 is returned.

---

## Data Sources

* The API system is asynchronous; delays are expected.

* Data sources:

  * - Matching Engine (most real-time)
  * - Memory (cached data)
  * - Database (persistent storage)

Some endpoints may use fallback chains like Memory → Database.

---

Specific error codes and messages are defined in the [Error Codes](./errors.md) section.
