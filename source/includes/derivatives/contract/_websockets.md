# t(:websocket)
## t(:websocketauthentication)
> t(:websocket_codequote_auth)

> t(:websocket_codequote_auth2)

```python--pybit
# based on: https://github.com/bybit-exchange/pybit/blob/master/pybit/_http_manager.py

import hmac
import json
import time
import websocket

ws_url = "wss://stream.bybit.com/realtime"

api_key = ""
api_secret = ""

# Generate expires.
expires = int((time.time() + 1) * 1000)

# Generate signature.
signature = str(hmac.new(
    bytes(api_secret, "utf-8"),
    bytes(f"GET/realtime{expires}", "utf-8"), digestmod="sha256"
).hexdigest())

# Authenticate with API.
ws.send(
    json.dumps({
        "op": "auth",
        "args": [api_key, expires, signature]
    })
)

ws = websocket.WebSocketApp(
    url=url,
    ...
)
```

t(:websocket_para_endpoint_contract)

<aside class="notice">
t(:websocket_aside_auth)
</aside>


t(:websocket_para_methods)

<aside class="notice">
t(:websocket_aside_signature)
</aside>

<aside class="warning">
t(:websocket_best_practices)
</aside>


## t(:heartbeat)
> t(:websocket_codequote_heartbeat)

```javascript
ws.send('{"op":"ping"}');
```

> t(:codequote_responseExample)

```javascript
// pong response sample for usdt perp and inverse
{
    "success": true,
    "ret_msg": "pong",
    "conn_id": "1a30f215-b7d2-4542-bac8-563a79963b35",
    "req_id": "",
    "op": "ping"
}
```


<aside class="warning">
t(:websocket_aside_heartbeat)
</aside>

<!-- 连接数限制
## t(:websocketlimit)
t(:websocket_para_limit)
-->


## t(:subscribe)
### t(:websocketfilters)
> t(:websocket_codequote_filters1)

```javascript
// Subscribing to the trade data for BTCUSD
ws.send('{"op":"subscribe","args":["publicTrade.BTCUSD"],"req_id": "customised_id"}}')
```

> t(:websocket_codequote_filters2)

```javascript
// Example: Subscribing to the trade data for BTCUSD and XRPUSD
ws.send('{"op":"subscribe","args":["publicTrade.BTCUSD", "publicTrade.XRPUSD"],"req_id": "customised_id"}')
```


t(:websocket_para_filters)

`ws.send('{"op": "subscribe", "args": ["topic.filter"],"req_id": "customised_id"}');`

t(:websocket_para_filters1)

`ws.send('{"op": "subscribe", "args": ["topic.filter", "topic.filter"],"req_id": "customised_id"}');`

t(:websocket_para_filters3)
t(:websocket_para_filter_resp)

### t(:websocketunsubfilters)
> t(:websocket_codequote_unsubfilters)

```javascript
// Unsubscribing from the trade data for ETHUSD
ws.send('{{"op":"subscribe","args":["books-25.BTCUSDT"]}')
```

t(:websocket_para_unsubfilters)

`ws.send('{"op": "unsubscribe", "args": ["topic.filter", "topic.filter"]});`

### t(:intervals)
t(:websocket_para_intervals)

## t(:websocketresponse)
> t(:websocket_codequote_response)

```javascript
{
  "success": true,
  "ret_msg": "",
  "conn_id": "0b12f925-0ab7-4ff8-afd4-c9661456b8fc",
  "request": {
    "op": "subscribe",
    "args": [
      "books-25.BTCUSDT"
    ]
  }
}
```

t(:websocket_para_response)



## t(:publictopics)
### t(:websocketOrderBookDepth)

<aside class="notice">
t(:websocket_aside_orderbook_L1)
</aside>

> t(:codequote_subscribe)

```javascript
ws.send('{"op": "subscribe", "req_id": "10110001", "args": ["books-25.BTCUSDT","books-200.BTCUSDT"]}')
```
> t(:codequote_snapshot)

```javascript
{
    "topic": "books-25.BTCUSDT",
    "type": "snapshot",
    "ts": 1668748553479,
    "data": {
        "s": "BTCUSDT",
        "b": [
            [
                "17053.00", //price
                "0.021" //size
            ],
            ....
            [
                "17016.50",
                "0.020"
            ],
        ],
        "a": [
            [
                "17054.00",
                "6.288"
            ],
            ....
            [
                "17166.50",
                "0.049"
            ]
        ]
    },
    "cs": 17550368
}
```


> t(:codequote_delta)

```javascript
{
    "topic": "books-25.BTCUSDT",
    "type": "delta",
    "ts": 1668748553556,
    "data": {
        "s": "BTCUSDT",
        "b": [],
        "a": [
            [
                "17168.00",
                "0.300"
            ],
            [
                "17070.00",
                "0"
            ]
        ]
    },
    "cs": 17550368,

}
```

t(:websocketOrderBook_contract)

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|ts |long |t(:row_comment_dv3_ts)  |
|s |string |t(:row_comment_symbol)  |
|b|array |t(:row_comment_resp_bid)    |
|a |array|t(:row_comment_resp_ask)  |
|cs |number |t(:row_comment_cross_seq) |
|type|string | snapshot/delta/reset|



### t(:websockettrade)

> t(:codequote_subscribe)

```javascript
ws.send('{"op": "subscribe", "req_id": "10110001", "args": ["trades-100.BTCUSDT"]}')
```

```python--pybit

```

> t(:codequote_responseExampleFormatAll)


```javascript
{
{
  "topic": "trades-100.BTCUSDT",
  "type": "delta",
  "data": {
    "s": "BTCUSDT",
    "d": [
      [
        "0-",
        "26574.50",
        "0.25",
        "2023-03-17T13:32:02Z",
        "a",
        "9ca02a95-7b16-5967-a333-57e9aa654746",
        "0"
      ],
      [
        "-",
        "26573.00",
        "0.75",
        "2023-03-17T13:32:02Z",
        "a",
        "25a1e946-0e2c-5e5d-b486-c6247ff50cad",
        "0"
      ]
    ]
  },
  "cs": 16250033,
  "ts": 1679059922985128
}
    
}
```

t(:websocket_para_trade_ud)

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|ts|long |t(:row_comment_dv3_ts)  |
|d |array| trade list |
|type|string | snapshot|
|t (trade list )|
|:----- |:-----|----- |:-----|
|0 |string |t(:row_comment_position_tick_direction)  |
|1 |string |t(:row_response_comment_price)  |
|2 |string |t(:row_comment_position_size)  |
|3 |long |t(:row_comment_trade_T)  |
|4 |string |t(:websocketTradeSide)    |
|5 |string |t(:row_response_comment_trade_id)  |
|6 |string |"0"|


### t(:websocketTicker_v3)
> t(:codequote_subscribe)

```javascript
ws.send('{"op": "subscribe", "req_id": "10110001", "args": ["tickers-100.BTCUSDT"]}')
```

```python--pybit

```

> t(:codequote_snapshot)

```javascript
{
    "topic": "tickers-100.BTCUSDT",
    "type": "snapshot",
    "data": {
        "s": "BTCUSDT",
        "p": "28214.50",
        "b1": "26754.00",
        "a1": "28201.00",
        "td": "0+",
        "p24": "27000.00",
        "pP": 44981,
        "h": "28580.00",
        "l": "27000.00",
        "p1": "28210.00",
        "to": "1482841986.627001",
        "v": "52683.009",
        "ft": "2023-03-22T16:00:00Z",
        "mp": "28179.66",
        "ip": "28179.66",
        "o": "0",
        "frgs": "0",
        "fr": 100,
        "pf": 100,
        "nh": 8,
        "ds": "0"
    },
    "cs": 17652420,
    "ts": 1679490241132846
}
```

> t(:codequote_delta)

```javascript
{
  "topic": "tickers-100.BTCUSDT",
  "type": "delta",
  "data": {
    "s": "BTCUSDT",
    "td": "0-",
    "pr": 79715,
    "to": "1618146770.2949994",
    "v": "63582.93699999",
    "fr": 100,
    "pf": 100
  },
  "cs": 16250032,
  "ts": 1679059922684958
}
```



t(:websocket_para_ticker_contract)

<aside class="warning">
t(:websocket_aside_instrumentInfo_contract)
</aside>


<p class="fake_header">t(:futuresResponseParameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|shorthand｜
|:----- |:-----|----- |:-----|
|symbol |string |t(:row_comment_symbol)  |s|
|tickDirection|string |t(:row_comment_position_tick_direction)  |td|
|price24hPcnt|string|t(:row_comment_resp_price_24h_pcnt) |pP|
|lastPrice |string |t(:row_comment_resp_last_price)  |p|
|prevPrice24h |string |t(:row_comment_resp_prev_price_24h)  |p24|
|highPrice24h |string |t(:row_comment_resp_high_price_24h)  |h|
|lowPrice24h |string |t(:row_comment_resp_low_price_24h)  |l|
|markPrice |string |t(:row_comment_resp_mark_price)  |mp|
|indexPrice |string |t(:row_comment_resp_index_price)  |ip|
|openInterest |string |t(:row_comment_resp_open_interest). t(:row_comment_slow_update)  |o|
|turnover24h |string |t(:row_comment_resp_turnover_24h)  |to|
|volume24h |string |t(:row_comment_resp_volume_24h)  |v|
|nextFundingTime |string |t(:row_comment_resp_next_funding_time_v3)  |ft|
|fundingRate |string |t(:row_comment_resp_funding_rate_v3) |fr|
|bid1Price|string|t(:row_comment_resp_bid_price) |b1|
|bid1Size|string|t(:row_comment_resp_bid_size) |-|
|ask1Price|string|t(:row_comment_resp_ask_price) |a1|
|ask1Size|string|t(:row_comment_resp_ask_size) |-|
|prevPrice1h |string |t(:row_comment_resp_prev_price_1h_v3)  |p1|
|ReduceOnly  |string |  ReduceOnly Status | ro|
|cs |long |t(:row_comment_tickers_cs)  |
|ts |long |t(:row_comment_dv3_ts)  |



### t(:websocketkline)
> t(:codequote_subscribe)

```javascript
ws.send('{"op":"subscribe","req_id": "10110001", "args":["candle.60.BTCUSDT"]}')
```

```python--pybit

```

> t(:codequote_responseExampleFormatAll)

```javascript
{
    "topic": "candle.1.BTCUSDT",
    "data": [
        {
            "start": 1679544960,
            "end": 1679545020,
            "period": "1",
            "open": 27398,
            "close": 27409,
            "high": 27409,
            "low": 27390,
            "volume": "5.07",
            "turnover": "138909.63",
            "confirm": false,
            "cs": 17657145
        }
    ],
    "ts": 1679544971586546
}
```

t(:websocket_para_kline_v3)

<aside class="notice">
t(:websocket_aside_klineV2)
</aside>

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|start|integer |t(:row_comment_startTime)    |
|end|integer |t(:row_comment_endTime)    |
|period|string|t(:row_comment_interval) |
|open|number |t(:row_comment_open)    |
|close|number |t(:row_comment_close)    |
|high|number |t(:row_comment_high)    |
|low|number |t(:row_comment_low)    |
|volume|string |t(:row_comment_resp_volume)    |
|turnover|string |t(:row_comment_resp_turnover)    |
|confirm|boolean |t(:row_comment_confirm)|
|cs|number |cross_seq|
|ts|long |t(:row_comment_dv3_ts)    |


### t(:websocketliquidation)
> t(:codequote_subscribe)

```javascript
ws.send('{"op":"subscribe","req_id": "10110001", "args":["liquidation.GALAUSDT"]}')
```

```python--pybit

```

> t(:codequote_responseExampleFormatAll)

```javascript
{
    "data": {
        "price": "0.03803",
        "side": "Buy",
        "size": "1637",
        "symbol": "GALAUSDT",
        "updatedTime": 1673251091822
    },
    "topic": "liquidation.GALAUSDT",
    "ts": 1673251091822,
    "type": "snapshot"
}
```

t(:websocketliquidation_para)

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|updatedTime|integer |t(:insurance_resp_updatedTime) |
|symbol|string |t(:row_comment_symbol) |
|side|string|t(:liquidation_side) |
|size|string |t(:execQty)  |
|price|string |t(:excPrice)  |


## t(:contract_privateTopic)
### t(:websocketposition)
> t(:codequote_subscribe)


```javascript
ws.send('{"op":"subscribe","req_id": "10110001","args":["contract.position"]}');
```

> t(:codequote_responseExampleFormatAll)

```javascript
{
    "topic": "contract.position",
    "data": [
        {
            "symbol": "BTCUSDT",
            "size": 10.8,
            "side": "Buy",
            "positionValue": 303483.25,
            "entryPrice": 28100.3,
            "liqPrice": 0.5,
            "bustPrice": 0.5,
            "leverage": 10,
            "positionMargin": 2997400.2,
            "unrealisedPnl": 33.7225,
            "autoAddMargin": 1,
            "cumRealisedPnl": 819.33264,
            "positionStatus": "Normal",
            "adlRankIndicator": 2,
            "tpSlMode": "Partial",
            "riskId": 1,
            "isolated": false,
            "positionMode": "MergedSingle",
            "positionIdx": 0
        }
        ]
}
```

t(:contract_websocketPosition)

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|symbol |string |t(:row_comment_symbol_v3)  |
|size |float32 |t(:row_comment_query_size_v3)  |
|side |string |t(:row_comment_query_side_v3)  |
|positionValue |float32 |t(:row_comment_query_positionValue_v3)  |
|entryPrice |float32 |t(:row_comment_query_entryPrice_v3)  |
|liqPrice |float32 |t(:contract_position_liqPrice)  |
|bustPrice |float32 |t(:contract_position_bustPrice)  |
|leverage |float32 |t(:row_comment_query_leverage_v3)  |
|positionMargin |float32 |t(:contract_position_positionBalance)  |
|unrealisedPnl |string |t(:row_comment_query_unrealisedPnl_v3)  |
|cumRealisedPnl |string |t(:row_comment_query_cumRealisedPnl_v3)  |
|autoAddMargin |integer |t(:contract_position_autoAddMargin)  |
|positionStatus |string |t(:row_comment_updated_at)  |
|positionIdx |integer |t(:row_comment_query_positionIdx_v3)  |
|riskId |integer |t(:row_comment_riskId)  |


### t(:websocketexecution)
> t(:codequote_subscribe)

```javascript
ws.send('{"op":"subscribe","req_id": "10110001","args":["contract.execution"]}');
```

> t(:codequote_responseExampleFormatAll)

```javascript
{
    "topic": "contract.execution",
    "data": [
        {
            "symbol": "BTCUSDT",
            "side": "Buy",
            "orderId": "789eb56a-c85d-11ed-a5d3-525400d110a3",
            "execId": "f7c92052-723e-5708-8afd-dce6608bad32",
            "orderLinkId": "",
            "execPrice": 28100,
            "orderQty": 1,
            "execType": "Trade",
            "execQty": 0.4,
            "execFee": -2.81,
            "leavesQty": 0.2,
            "isMaker": true,
            "execTime": "2023-03-22T02:58:51.906815Z"
        }
    ]
}
```

t(:contract_websocketExecution)


<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|symbol |string |t(:row_comment_symbol_v3)   |
|side |string |t(:row_comment_query_side_v3)  |
|orderId |string |t(:row_comment_query_orderId_v3) |
|execId |string |t(:row_comment_query_execId_v3)  |
|orderLinkId |string |t(:row_comment_query_orderLinkId_v3)  |
|execPrice |float32 |t(:row_comment_query_execPrice_v3)  |
|execQty |float32 |t(:row_comment_query_execQty_v3)  |
|execType |string |t(:row_comment_query_execType_wss_contract_v3)  |
|execFee |float32 |t(:row_comment_query_execFee_v3)  |
|leavesQty |string |t(:row_comment_query_leavesQty_v3)  |
|execTime |string |t(:row_comment_query_execTime_v3)  |


### t(:websocketOrder)
> t(:codequote_subscribe)

```javascript
ws.send('{"op":"subscribe","req_id": "10110001","args":["contract.order"]}');
```

> t(:codequote_responseExampleFormatAll)

```javascript
{
    "topic": "contract.order",
    "data": [
        {
            "symbol": "BTCUSDT",
            "orderId": "789eb56a-c85d-11ed-a5d3-525400d110a3",
            "orderLinkId": "",
            "side": "Buy",
            "orderType": "Limit",
            "price": 28100,
            "qty": 1,
            "leavesQty": 0.2,
            "lastExecPrice": 28100,
            "cumExecQty": 0.8,
            "cumExecValue": 22479.998,
            "cumExecFee": -5.62,
            "timeInForce": "GoodTillCancel",
            "orderStatus": "PartiallyFilled",
            "takeProfit": 0,
            "stopLoss": 0,
            "createTime": "2023-03-22T02:58:49.954324094Z",
            "updateTime": "2023-03-22T02:58:51.911163835Z",
            "reduceOnly": false,
            "closeOnTrigger": false,
            "positionIdx": 0
        }
    ]
}
```

t(:contract_websocketOrder)


<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|symbol |string |t(:row_comment_symbol_v3)   |
|orderId |string |t(:row_comment_query_orderId_v3) |
|orderLinkId |string |t(:row_comment_query_orderLinkId_v3)  |
|side |string |t(:row_comment_query_side_v3)  |
|orderType |string |t(:row_comment_query_orderType_v3)  |
|stopOrderType |string |t(:row_comment_query_stopOrderType_v3)  |
|price |float32 |t(:row_comment_query_price_v3)  |
|qty |float32 |t(:row_comment_query_qty_v3)  |
|leavesQty |float32 |t(:leavesQty)  |
|lastExecPrice |float32 |t(:lastExecPrice)  |
|cumExecQty |float32 |t(:cumExecQty)  |
|cumExecValue |float32 |t(:cumExecValue)  |
|timeInForce |string |t(:row_comment_query_timeInForce_v3)  |
|orderStatus |string |t(:row_comment_query_orderStatus_v3)  |
|takeProfit |string |t(:row_comment_query_takeProfit_v3)  |
|stopLoss |string |t(:row_comment_query_stopLoss_v3)  |
|createdTime |string |t(:row_comment_query_createdTime_v3)  |
|updatedTime |string |t(:row_comment_query_updatedTime_v3)  |
|reduceOnly |bool |t(:row_comment_query_reduceOnly_v3)  |
|closeOnTrigger |bool |t(:row_comment_query_closeOnTrigger_v3)  |


### t(:websocketwallet)
> t(:codequote_subscribe)

```javascript
ws.send('{"op": "subscribe", "req_id": "10110001", "args": ["contract.wallet"]}')
```

> t(:codequote_responseExampleFormatAll)

```javascript
{
    "topic": "contract.wallet",
    "data": [
        {
            "coin": "USDT",
            "equity": 3000527,
            "walletBalance": 3000819.5,
            "availableBalance": 2966554.8,
            "positionMargin": 30845.646,
            "orderMargin": 3419.0366,
            "unrealisedPnl": -292.469,
            "cumRealisedPnl": 819.33264
        }
    ]
}
```

t(:contract_websocketWallet)

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|coin |string |t(:row_comment_query_coin_coin_v3)    |
|equity |float32 |t(:row_comment_query_coin_equity_v3)    |
|walletBalance |float32 |t(:row_comment_query_coin_walletBalance_v3)    |
|availableBalance |float32 |t(:contract_walletAvailableBalance)    |
|positionMargin |float32 |t(:contract_walletPositionMargin)    |
|orderMargin |float32 |t(:contract_walletOrderMargin)    |
|unrealisedPnl |float32 |t(:row_comment_query_coin_unrealisedPnl_v3)    |
|cumRealisedPnl |float32 |t(:row_comment_query_coin_cumRealisedPnl_v3)    |
