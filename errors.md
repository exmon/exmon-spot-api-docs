# EXMON API Error Codes

This document describes error responses returned by the EXMON Public API.

---

## General Error Format

All errors are returned in JSON format.

Example:
```
{
  "code": -1000,
  "message": "Invalid request parameters"
}
```
---

## Error Fields

Field | Type | Description
------------ | ------------ | ------------
code | integer | Numeric error code
message | string | Human-readable error description

---

## Common Error Codes

Code | Description
------------ | ------------
-1000 | Invalid request parameters
-1001 | Missing required parameter
-1002 | Invalid parameter value
-1003 | Invalid currency pair
-1004 | Invalid limit value
-1005 | Invalid quantity
-1006 | Invalid request format
-1007 | Request timeout
-1008 | Too many requests (rate limit exceeded)
-1009 | Endpoint not found
-1010 | Internal server error

---

## HTTP Status Mapping

HTTP Code | Description
------------ | ------------
200 | Success
400 | Bad request (invalid parameters)
404 | Endpoint not found
422 | Validation error
429 | Rate limit exceeded
500 | Internal server error
502 / 503 | Temporary backend error

---

## Notes

* Errors may be returned for any endpoint
* The `code` field should be used for programmatic handling
* The `message` field is intended for debugging and human readability
* Clients should always check both HTTP status and response body
* In case of timeout or server error, request execution status may be unknown
