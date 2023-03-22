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
ws.send('{"op":"unsubscribe","args":["publicTrade.ETHUSD"],"req_id": "customised_id"}')
```

t(:websocket_para_unsubfilters)

`ws.send('{"op": "unsubscribe", "args": ["topic.filter", "topic.filter"],"req_id": "customised_id"}');`

### t(:intervals)
t(:websocket_para_intervals)

## t(:websocketresponse)
> t(:websocket_codequote_response)

```javascript
{
  "success": true,
  "ret_msg": "",
  "conn_id": "fd79c21d-df3c-4439-aaab-c802bcb60e02",
  "req_id": "customize_00001",
  "op": "subscribe"
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
    "p": "26577.50",
    "b1": "26589.50",
    "a1": "27075.00",
    "td": "0-",
    "p2": "24612.50",
    "pr": 79837,
    "h": "27195.00",
    "l": "24597.00",
    "p1": "26621.50",
    "to": "1618114874.7449994",
    "v": "63581.73699999",
    "ft": "2023-03-17T16:00:00Z",
    "mp": "26565.77",
    "xp": "26566.05",
    "o": "0",
    "frgs": "0",
    "fr": 100,
    "pf": 100,
    "nh": 8,
    "ds": "0"
  },
  "cs": 16250028,
  "ts": 1679059921485225
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

> t(:codequote_option)


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
  "topic": "candle.60.BTCUSDT",
  "data": [
    {
      "start": 1679061600,
      "end": 1679065200,
      "period": "60",
      "open": 26452,
      "close": 26457.5,
      "high": 26638.5,
      "low": 26383.5,
      "volume": "1579.69",
      "turnover": "41925473.635",
      "confirm": false,
    }
  ],
  "ts": 1679063665196390
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
ws.send('{"op":"subscribe","req_id": "10110001","args":["user.position.contractAccount"]}');
```

> t(:codequote_responseExampleFormatAll)

```javascript
{
    "topic": "user.position.contractAccount",
    "data": [
        {
            "positionIdx": 0,
            "riskId": 1,
            "symbol": "BTCUSDT",
            "side": "Buy",
            "size": "0.024",
            "positionValue": "394.55123078",
            "entryPrice": "16439.63461538",
            "tradeMode": 0,
            "autoAddMargin": 0,
            "leverage": "3",
            "positionBalance": "131.67490005",
            "liqPrice": "0.50",
            "bustPrice": "0.50",
            "takeProfit": "0.00",
            "stopLoss": "0.00",
            "trailingStop": "0.00",
            "unrealisedPnl": "32.57676922",
            "createdTime": "1640056352777",
            "updatedTime": "1671002545179",
            "tpSlMode": "Partial",
            "sessionAvgPrice": "0.00",
            "positionStatus": "Normal",
            "occClosingFee": "0.0000072",
            "markPrice": "17797.00",
            "cumRealisedPnl": "44834.01605397",
            "activePrice": "0.00",
            "riskLimitValue": "2000000",
            "positionMM": "0.00006",
            "positionIM": "3.9455123078"
        }
```

t(:contract_websocketPosition)

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|positionIdx |integer |t(:row_comment_query_positionIdx_v3)  |
|riskId |integer |t(:row_comment_riskId)  |
|riskLimitValue |string |t(:contract_position_riskLimitValue)  |
|symbol |string |t(:row_comment_symbol_v3)  |
|side |string |t(:row_comment_query_side_v3)  |
|size |string |t(:row_comment_query_size_v3)  |
|positionValue |string |t(:row_comment_query_positionValue_v3)  |
|entryPrice |string |t(:row_comment_query_entryPrice_v3)  |
|markPrice |string |t(:contract_position_markPrice)  |
|tradeMode |integer |t(:contract_position_tradeMode)  |
|autoAddMargin |integer |t(:contract_position_autoAddMargin)  |
|leverage |string |t(:row_comment_query_leverage_v3)  |
|positionBalance |string |t(:contract_position_positionBalance)  |
|positionStatus |string |t(:row_comment_updated_at)  |
|sessionAvgPrice |string |t(:row_comment_query_sessionAvgPrice_v3)  |
|occClosingFee |string |t(:row_comment_occ_closing_fee)  |
|liqPrice |string |t(:contract_position_liqPrice)  |
|bustPrice |string |t(:contract_position_bustPrice)  |
|takeProfit |string |t(:row_comment_query_takeProfit_v3)  |
|stopLoss |string |t(:row_comment_query_stopLoss_v3)  |
|trailingStop |string |t(:row_comment_query_trailingStop_v3)  |
|unrealisedPnl |string |t(:row_comment_query_unrealisedPnl_v3)  |
|activePrice | string | t(:account_row_comment_activePrice_v3) |
|positionIM |string |t(:row_comment_query_positionIM_v3)  |
|positionMM |string |t(:row_comment_query_positionMM_v3)  |
|cumRealisedPnl |string |t(:row_comment_query_cumRealisedPnl_v3)  |
|createdTime |number |t(:row_comment_query_createdTime_v3)  |
|updatedTime |number |t(:row_comment_query_updatedTime_v3)  |
|tpslMode |string |t(:row_comment_query_tpslMode_v3)  |


### t(:websocketexecution)
> t(:codequote_subscribe)

```javascript
ws.send('{"op":"subscribe","req_id": "10110001","args":["user.execution.contractAccount"]}');
```

> t(:codequote_responseExampleFormatAll)

```javascript
{
    "topic": "user.execution.contractAccount",
    "data": [
        {
            "symbol": "BITUSDT",
            "execFee": "0.02022",
            "execId": "beba036f-9fb4-59a7-84b7-2620e5d13e1c",
            "execPrice": "0.674",
            "execQty": "50",
            "execType": "Trade",
            "execValue": "33.7",
            "feeRate": "0.0006",
            "lastLiquidityInd": "RemovedLiquidity",
            "leavesQty": "0",
            "orderId": "ddbea432-2bd7-45dd-ab42-52d920b8136d",
            "orderLinkId": "b001",
            "orderPrice": "0.707",
            "orderQty": "50",
            "orderType": "Market",
            "stopOrderType": "UNKNOWN",
            "side": "Buy",
            "execTime": "1659057535081",
            "closedSize": "0"
        }
    ]
}
```

t(:contract_websocketExecution)


<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|symbol |string |t(:row_comment_symbol_v3)   |
|execFee |string |t(:row_comment_query_execFee_v3)  |
|execId |string |t(:row_comment_query_execId_v3)  |
|execPrice |string |t(:row_comment_query_execPrice_v3)  |
|execQty |string |t(:row_comment_query_execQty_v3)  |
|execType |string |t(:row_comment_query_execType_wss_contract_v3)  |
|execValue |string |t(:row_comment_query_execValue_v3)  |
|feeRate |string |t(:row_comment_query_feeRate_v3)  |
|lastLiquidityInd |string |t(:row_comment_query_lastLiquidityInd_v3)  |
|leavesQty |string |t(:row_comment_query_leavesQty_v3)  |
|orderId |string |t(:row_comment_query_orderId_v3) |
|orderLinkId |string |t(:row_comment_query_orderLinkId_v3)  |
|orderPrice |string |t(:row_comment_query_price_v3)  |
|orderQty |string |t(:row_comment_query_qty_v3)  |
|orderType |string |t(:row_comment_query_orderType_v3)  |
|stopOrderType |string |t(:row_comment_query_stopOrderType_v3)  |
|side |string |t(:row_comment_query_side_v3)  |
|execTime |string |t(:row_comment_query_execTime_v3)  |
|closedSize |string |t(:closedSize)  |


### t(:websocketOrder)
> t(:codequote_subscribe)

```javascript
ws.send('{"op":"subscribe","req_id": "10110001","args":["user.order.contractAccount"]}');
```

> t(:codequote_responseExampleFormatAll)

```javascript
{
    "topic": "user.order.contractAccount",
    "data": [
        {
            "symbol": "BTCUSD",
            "orderId": "ee013d82-fafc-4504-97b1-d92aca21eedd",
            "side": "Buy",
            "orderType": "Market",
            "stopOrderType": "UNKNOWN",
            "price": "21920.00",
            "qty": "200",
            "timeInForce": "ImmediateOrCancel",
            "orderStatus": "Filled",
            "triggerPrice": "0.00",
            "orderLinkId": "inv001",
            "createdTime": "1661338622771",
            "updatedTime": "1661338622775",
            "takeProfit": "0.00",
            "stopLoss": "0.00",
            "tpTriggerBy": "UNKNOWN",
            "slTriggerBy": "UNKNOWN",
            "triggerBy": "UNKNOWN",
            "reduceOnly": false,
            "closeOnTrigger": false,
            "triggerDirection": 0,
            "leavesQty": "0",
            "lastExecQty": "200",
            "lastExecPrice": "21282.00",
            "cumExecQty": "200",
            "cumExecValue": "0.00939761"
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
|side |string |t(:row_comment_query_side_v3)  |
|orderType |string |t(:row_comment_query_orderType_v3)  |
|stopOrderType |string |t(:row_comment_query_stopOrderType_v3)  |
|price |string |t(:row_comment_query_price_v3)  |
|qty |string |t(:row_comment_query_qty_v3)  |
|timeInForce |string |t(:row_comment_query_timeInForce_v3)  |
|orderStatus |string |t(:row_comment_query_orderStatus_v3)  |
|triggerPrice |string |t(:row_comment_query_triggerPrice_v3)  |
|orderLinkId |string |t(:row_comment_query_orderLinkId_v3)  |
|createdTime |string |t(:row_comment_query_createdTime_v3)  |
|updatedTime |string |t(:row_comment_query_updatedTime_v3)  |
|takeProfit |string |t(:row_comment_query_takeProfit_v3)  |
|stopLoss |string |t(:row_comment_query_stopLoss_v3)  |
|t(:contract_param_executionTpTriggerBy) |string |t(:row_comment_query_tpTriggerBy_v3)  |
|t(:contract_parm_executionSlTriggerBy) |string |t(:row_comment_query_slTriggerBy_v3)  |
|basePrice |string |t(:row_comment_query_basePrice_v3)  |
|t(:contract_param_executionTriggerBy) |string |t(:row_comment_query_triggerBy_v3)  |
|reduceOnly |bool |t(:row_comment_query_reduceOnly_v3)  |
|closeOnTrigger |bool |t(:row_comment_query_closeOnTrigger_v3)  |
|leavesQty |string |t(:leavesQty)  |
|lastExecPrice |string |t(:lastExecPrice)  |
|lastExecQty |string |t(:lastExecQty)  |
|cumExecQty |string |t(:cumExecQty)  |
|cumExecValue |string |t(:cumExecValue)  |


### t(:websocketwallet)
> t(:codequote_subscribe)

```javascript
ws.send('{"op": "subscribe", "req_id": "10110001", "args": ["user.wallet.contractAccount"]}')
```

> t(:codequote_responseExampleFormatAll)

```javascript
{
    "topic": "user.wallet.contractAccount",
    "data": [
        {
            "coin": "USDT",
            "equity": "610.3984319",
            "walletBalance": "609.7384319",
            "positionMargin": "4.7582882",
            "availableBalance": "604.9801437",
            "orderMargin": "0",
            "unrealisedPnl": "0.66",
            "cumRealisedPnl": "-0.2615681"
        }
    ]
}
```

t(:contract_websocketWallet)

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|coin |string |t(:row_comment_query_coin_coin_v3)    |
|equity |string |t(:row_comment_query_coin_equity_v3)    |
|walletBalance |string |t(:row_comment_query_coin_walletBalance_v3)    |
|positionMargin |string |t(:contract_walletPositionMargin)    |
|availableBalance |string |t(:contract_walletAvailableBalance)    |
|orderMargin |string |t(:contract_walletOrderMargin)    |
|unrealisedPnl |string |t(:row_comment_query_coin_unrealisedPnl_v3)    |
|cumRealisedPnl |string |t(:row_comment_query_coin_cumRealisedPnl_v3)    |
