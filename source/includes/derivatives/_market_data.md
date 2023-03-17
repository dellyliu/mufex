# t(:marketdata)
t(:market_para_auth_v3)

### t(:dv_orderbook)
> t(:codequote_curlExample)

```console
curl GET 'https://api-testnet.mufex.com/fapi/public/v1/market/order-book?category=linear&symbol=BTCUSDT'
```

```python--pybit

```

> t(:codequote_responseExample)

```javascript
{
    "code": 0,
    "message": "OK",
    "data":  {
        "s": "BTCUSDT",
        "b": [
            [
                "28806",
                "0.06"
            ],
            [
                "28807",
                "5.005"
            ]
        ],
        "a": [
            [
                "29004",
                "0.001"
            ],
            [
                "29012",
                "0.017"
            ]
        ],
        "ts": 1653638043149,
        "u": 4912426
    },
    "ext_info": {},
    "time": 1679034720118
}
```

t(:market_para_orderbook)  
t(:dv_orderbookPara)

<aside class="notice">
t(:market_aside_orderbook)
</aside>

<p class="fake_header">t(:httprequest)</p>
GET
<code><span id=dvOrderbook>/fapi/public/v1/market/order-book</span></code>
<button class="clipboard_button" data-clipboard-action="copy" data-clipboard-target="#dvOrderbook"><img src="/images/copy_to_clipboard.png" height=15 width=15></img></button>

<p class="fake_header">t(:requestparameters)</p>
|t(:column_parameter)|t(:column_required)|t(:column_type)|t(:column_comments)|
|:----- |:-------|:-----|------ |
|symbol |<b>true</b> |string |t(:row_comment_symbol) |
|limit |false |int |t(:dv_orderbookLimit) |

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|s |string |t(:row_comment_symbol) |
|b |array |t(:dv_orderbookBids) |
|a |array |t(:dv_orderbookAsks) |
|ts |integer |t(:dv_orderbookTimeStamp) |
|u |string |t(:dv_orderbookUpdateId) |


### t(:dv_querykline)
> t(:codequote_curlExample)

```console
curl GET 'https://api-testnet.mufex.com/fapi/public/v1/market/kline?category=linear&symbol=BTCUSDT&interval=D&start=1652112000000&end=1652544000000'
```

```python--pybit

```

> t(:codequote_responseExample)

```javascript
{
    "code": 0,
    "message": "OK",,
    "data": {
      "category":"linear",
      "symbol":"BTCUSDT",
      "interval":"1",
      "list":[
      "1621162800000",
      "49592.43",
      "49644.91",
      "49342.37",
      "49349.42",
      "1451.59",
      "2.4343353100000003"
    ]
    },
    "ext_info": {},
    "time": 1669802294719
}
```

t(:market_para_querykline)

<p class="fake_header">t(:httprequest)</p>
GET
<code><span id=dvkline>/fapi/public/v1/market/kline</span></code>
<button class="clipboard_button" data-clipboard-action="copy" data-clipboard-target="#dvkline"><img src="/images/copy_to_clipboard.png" height=15 width=15></img></button>

<p class="fake_header">t(:requestparameters)</p>
|parameter|t(:column_required)|t(:column_type)|t(:column_comments)|
|:----- |:-------|:-----|----- |
|category |<b>true</b> |string |t(:dv_category)t(:dv_categorySuffix_1) |
|symbol |<b>true</b> |string |t(:row_comment_symbol) |
|<a href="#kline-interval-interval">interval</a> |<b>true</b> |string |t(:dv_klineInterval) |
|start |<b>true</b> |integer |t(:row_comment_startTime_ms) |
|end |<b>true</b> |integer |t(:row_comment_endTime_ms) |
|limit |false |integer |t(:row_comment_limit_200) |

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|category |string |t(:dv_category)t(:dv_categorySuffix_1) |
|symbol |string |t(:row_comment_symbol) |
|list |string[] |t(:row_comment_kline_list) |


### t(:dv_tickerHead)
> t(:codequote_curlExample)

```console
curl GET 'https://api-testnet.mufex.com/fapi/public/v1/market/tickers?category=linear&symbol=BTCUSDT'
```

```python--pybit

```

> t(:codequote_responseExample)

```javascript
{
    "code": 0,
    "message": "OK",
    "data":  {
        "category": "linear",
        "list": [
            {
                "symbol": "BTCUSDT",
                "bidPrice": "19255",
                "askPrice": "19255.5",
                "lastPrice": "19255.50",
                "lastTickDirection": "ZeroPlusTick",
                "prevPrice24h": "18634.50",
                "price24hPcnt": "0.033325",
                "highPrice24h": "19675.00",
                "lowPrice24h": "18610.00",
                "prevPrice1h": "19278.00",
                "markPrice": "19255.00",
                "indexPrice": "19260.68",
                "openInterest": "48069.549",
                "turnover24h": "4686694853.047006",
                "volume24h": "243730.252",
                "fundingRate": "0.0001",
                "nextFundingTime": "1663689600000"
            }
        ]
    },
    "ext_info": {},
    "time": 1663670053454
}


```

t(:dv_marketTickerPara)

<p class="fake_header">t(:httprequest)</p>
GET
<code><span id=dvtickers>/fapi/public/v1/market/tickers</span></code>
<button class="clipboard_button" data-clipboard-action="copy" data-clipboard-target="#dvtickers"><img src="/images/copy_to_clipboard.png" height=15 width=15></img></button>

<p class="fake_header">t(:requestparameters)</p>
|t(:column_parameter)|t(:column_required)|t(:column_type)|t(:column_comments)|
|:----- |:-------|:-----|----- |
|category |<b>true</b> |string |t(:dv_category)t(:dv_categorySuffix_2) |
|symbol |false |string |t(:dv_tickerSymbol) |


<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
| category |string |t(:dv_category) |
| price24hPcnt |string |t(:row_comment_resp_price_24h_pcnt) |
| nextFundingTime |string |t(:row_comment_resp_next_funding_time) |
| indexPrice |string |t(:row_comment_resp_index_price) |
| prevPrice24h |string |t(:row_comment_resp_prev_price_24h) |
| openInterest |string |t(:row_comment_resp_open_interest) |
| underlyingPrice |string |t(:usdcUnderlyingPrice) |
| volume24h |string |t(:row_comment_resp_volume_24h) |
| symbol |string |t(:row_comment_symbol) |
| lastTickDirection | string |t(:row_comment_tick_direction) |
| lastPrice |string |t(:row_comment_resp_last_price) |
| totalVolume |string |t(:row_comment_resp_total_volume) |
| bidPrice |string |t(:bidPrice) |
| totalTurnover |string |t(:row_comment_resp_total_turnover) |
| turnover24h |string |t(:row_comment_resp_turnover_24h) |
| askPrice |string |t(:askPrice) |
| fundingRate |string |t(:row_comment_funding_rate) |
| bidSize |string |t(:bidSize) |
| highPrice24h |string |t(:row_comment_resp_high_price_24h) |
| askSize |string |t(:askSize) |
| prevPrice1h |string |t(:row_comment_resp_prev_price_1h) |
| markPrice |string |t(:row_comment_resp_mark_price) |
| lowPrice24h |string |t(:row_comment_resp_low_price_24h) |



### t(:dv_instrHead)
> t(:codequote_curlExample)

```console
curl GET 'https://api-testnet.mufex.com/fapi/public/v1/instruments?category=linear&symbol=BTCUSDT'
```

```python--pybit

```

> t(:codequote_responseExample)

```javascript
{
    "code": 0,
    "message": "OK",
    "data":  {
        "category": "linear",
        "list": [
            {
                "symbol": "BTCUSDT",
                "contractType": "LinearPerpetual",
                "status": "Trading",
                "baseCoin": "BTC",
                "quoteCoin": "USDT",
                "launchTime": "1584230400000",
                "deliveryTime": "0",
                "deliveryFeeRate": "",
                "priceScale": "2",
                "leverageFilter": {
                    "minLeverage": "1",
                    "maxLeverage": "100.00",
                    "leverageStep": "0.01"
                },
                "priceFilter": {
                    "minPrice": "0.50",
                    "maxPrice": "999999.00",
                    "tickSize": "0.50"
                },
                "lotSizeFilter": {
                    "maxTradingQty": "100.000",
                    "minTradingQty": "0.001",
                    "qtyStep": "0.001",
                    "postOnlyMaxOrderQty": "1000.000"
                },
                "unifiedMarginTrade": true,
                "fundingInterval": 480,
                "settleCoin": "USDT"
            }
        ],
        "nextPageCursor": ""
    },
    "ext_info": {},
    "time": 1670838442302
}

```

t(:dv_marketInstrPara)

<p class="fake_header">t(:httprequest)</p>
GET
<code><span id=dvinstru>/fapi/public/v1/instruments</span></code>
<button class="clipboard_button" data-clipboard-action="copy" data-clipboard-target="#dvinstru"><img src="/images/copy_to_clipboard.png" height=15 width=15></img></button>

<p class="fake_header">t(:requestparameters)</p>
|parameter|t(:column_required)|t(:column_type)|t(:column_comments)|
|:----- |:-------|:-----|----- |
|category |<b>true</b> |string |t(:dv_category)t(:dv_categorySuffix_2) |
|symbol |false |string |t(:row_comment_symbol) |
|limit |false |string |t(:row_comment_limit_500_1000) |
|cursor |false |string |t(:dv_cursor) |

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|category |string |t(:dv_category)t(:dv_categorySuffix_2) |
|symbol |string |t(:row_comment_symbol) |
|contractType |string |t(:dv_instrContractType) |
|status |string |t(:row_response_comment_status) |
|baseCoin |string |t(:dv_instrBaseCoin) |
|quoteCoin |string |t(:dv_instrQuoteCoin) |
|settleCoin |string |t(:dv_instrSettleCoin) |
|optionsType |string |t(:dv_OptionType) |
|launchTime |string |t(:dv_instrLaunchTime) |
|deliveryTime |string |t(:dv_instrDeliveryTime) |
|deliveryFeeRate |string |t(:deliveryFeeRate) |
|priceScale |string |t(:dv_instrPriceScale) |
|leverageFilter> minLeverage |string |t(:minLeverage) |
|leverageFilter> maxLeverage |string |t(:maxLeverage) |
|leverageFilter> leverageStep |string |t(:leverageStep) |
|priceFilter> minPrice |string |t(:minPrice) |
|priceFilter> maxPrice |string |t(:maxPrice) |
|priceFilter> tickSize |string |t(:tickSize) |
|lotSizeFilter> maxOrderQty |string |t(:dv_instrMaxOrderQty) |
|lotSizeFilter> minOrderQty |string |t(:dv_instrMinOrderQty) |
|lotSizeFilter> qtyStep |string |t(:qtyStep) |
|lotSizeFilter> postOnlyMaxOrderQty |string |t(:dv_instrument_postOnlyMaxOrderQty) |
|unifiedMarginTrade |boolean |t(:dv3_instrument_unifiedMarginTrade) |
|fundingInterval |integer |t(:dv_instrument_fundingInterval) |
|nextPageCursor |string |t(:dv_cursor) |


### t(:dv_markpricekline)
> t(:codequote_curlExample)

```console
curl --location --request GET 'https://api-testnet.mufex.com/fapi/public/v1/market/mark-price-kline?category=linear&symbol=BTCUSDT&interval=D&start=1652112000000&end=1652544000000'
```

```python--pybit

```

> t(:codequote_responseExample)

```javascript
{
    "code": 0,
    "message":"OK",
    "data": {
      "category":"linear",
      "symbol":"BTCUSDT",
      "interval":"1",
      "list":[
      "1621162800",
      "49592.43",
      "49644.91",
      "49342.37",
      "49349.42",
    ]
    },
    "ext_info": {},
    "time": 1669802294719
}
```

t(:linear_query_mark_price_kline_v3)

<p class="fake_header">t(:httprequest)</p>
GET
<code><span id=dvmarkkline>/fapi/public/v1/market/mark-price-kline</span></code>
<button class="clipboard_button" data-clipboard-action="copy" data-clipboard-target="#dvmarkkline"><img src="/images/copy_to_clipboard.png" height=15 width=15></img></button>

<p class="fake_header">t(:requestparameters)</p>
|parameter|t(:column_required)|t(:column_type)|t(:column_comments)|
|:----- |:-------|:-----|----- |
|category |<b>true</b> |string |t(:dv_category)t(:dv_categorySuffix_1) |
|symbol |<b>true</b> |string |t(:row_comment_symbol) |
|<a href="#kline-interval-interval">interval</a> |<b>true</b> |string |t(:dv_klineInterval) |
|start |<b>true</b> |integer |t(:row_comment_startTime_ms) |
|end |<b>true</b> |integer |t(:row_comment_endTime_ms) |
|limit |false |integer |t(:row_comment_limit_200) |

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|category |string |t(:dv_category)t(:dv_categorySuffix_1) |
|symbol |string |t(:row_comment_symbol) |
|list |string[] |t(:row_comment_mark_kline_list) |

### t(:dv_indexpricekline)
> t(:codequote_curlExample)

```console
curl --location --request GET 'https://api-testnet.mufex.com/fapi/public/v1/market/index-price-kline?category=linear&symbol=BTCUSDT&interval=D&start=1652112000000&end=1652544000000'
```

```python--pybit

```

> t(:codequote_responseExample)

```javascript
{
    "code": 0,
    "message": "OK",
    "data": {
      "category":"linear",
      "symbol":"BTCUSDT",
      "interval":"1",
      "list":[
      "1621162800",
      "49592.43",
      "49644.91",
      "49342.37",
      "49349.42",
      "1451.59",
      "2.4343353100000003"
    ]
  },
  "ext_info": {},
  "time": 1679025663662
}
```
t(:queryindexpricekline)

<p class="fake_header">t(:httprequest)</p>
GET
<code><span id=dvindexkline>/fapi/public/v1/market/index-price-kline</span></code>
<button class="clipboard_button" data-clipboard-action="copy" data-clipboard-target="#dvindexkline"><img src="/images/copy_to_clipboard.png" height=15 width=15></img></button>

<p class="fake_header">t(:requestparameters)</p>
|parameter|t(:column_required)|t(:column_type)|t(:column_comments)|
|:----- |:-------|:-----|----- |
|category |<b>true</b> |string |t(:dv_category)t(:dv_categorySuffix_1) |
|symbol |<b>true</b> |string |t(:row_comment_symbol) |
|<a href="#kline-interval-interval">interval</a> |<b>true</b> |string |t(:dv_klineInterval) |
|start |<b>true</b> |integer |t(:row_comment_startTime_ms) |
|end |<b>true</b> |integer |t(:row_comment_endTime_ms) |
|limit |false |integer |t(:row_comment_limit_200) |

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|category |string |t(:dv_category)t(:dv_categorySuffix_1) |
|symbol |string |t(:row_comment_symbol) |
|list |string[] |t(:row_comment_kline_list) |



### t(:dv_historyFundingRateHead)
> t(:codequote_curlExample)

```console
curl GET 'https://api-testnet.mufex.com//fapi/public/v1/funding-rate-history?category=linear&symbol=BTCUSDT&startTime=1652112000000&endTime=1652198400000'
```

```python--pybit

```

> t(:codequote_responseExample)

```javascript
{
    "code": 0,
    "message": "OK",
    "data":  {
        "category": "linear",
        "list": [
            {
                "symbol": "BTCUSDT",
                "fundingRate": "0.0001",
                "fundingRateTimestamp": "1657728000000"
            },
            {
                "symbol": "BTCUSDT",
                "fundingRate": "0.0001",
                "fundingRateTimestamp": "1657699200000"
            }
        ]
    },
    "ext_info": {},
    "time": 1657782323371
}
```
t(:market_para_fundingRate)

<p class="fake_header">t(:httprequest)</p>
GET
<code><span id=dvhistfundrate>/fapi/public/v1/funding-rate-history</span></code>
<button class="clipboard_button" data-clipboard-action="copy" data-clipboard-target="#dvhistfundrate"><img src="/images/copy_to_clipboard.png" height=15 width=15></img></button>

<p class="fake_header">t(:requestparameters)</p>
|parameter|t(:column_required)|t(:column_type)|t(:column_comments)|
|:----- |:-------|:-----|----- |
|category |<b>true</b> |string |t(:dv_category)t(:dv_categorySuffix_3) |
|symbol |<b>true</b> |string |t(:row_comment_symbol) |
|startTime |false |integer |t(:row_comment_startTime_ms) |
|endTime |false |integer |t(:row_comment_endTime_ms) |
|limit |false |integer |t(:row_comment_limit_200) |


<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|category |string |t(:dv_category)t(:dv_categorySuffix_3) |
|symbol |string |t(:row_comment_symbol) |
|fundingRate |string |t(:row_comment_funding_rate) |
|fundingRateTimestamp |string |t(:row_comment_funding_rate_timestamp) |


### t(:dv_riskLimitHead)
> t(:codequote_curlExample)

```console
curl GET 'https://api-testnet.mufex.com/fapi/public/v1/position-risk?category=linear&symbol=BTCUSDT'
```

```python--pybit

```

> t(:codequote_responseExample)

```javascript
{
    "code": 0,
    "message": "OK",
    "data":  {
        "category": "linear",
        "list": [
            {
                "id": 1,
                "symbol": "BTCUSDT",
                "limit": "2000000",
                "maintainMargin": "0.005",
                "initialMargin": "0.01",
                "section": [
                    "1",
                    "3",
                    "5",
                    "10",
                    "25",
                    "50",
                    "80"
                ],
                "isLowestRisk": 1,
                "maxLeverage": "100.00"
            }
        ]
    },
    "ext_info": {},
    "time": 1669802294719
}
```

t(:dv_riskLimitHead)

<p class="fake_header">t(:httprequest)</p>
GET
<code><span id=dvrisklimit>fapi/public/v1/position-risk</span></code>
<button class="clipboard_button" data-clipboard-action="copy" data-clipboard-target="#dvrisklimit"><img src="/images/copy_to_clipboard.png" height=15 width=15></img></button>

<p class="fake_header">t(:requestparameters)</p>
|t(:column_parameter)|t(:column_required)|t(:column_type)|t(:column_comments)|
|:----- |:-------|:-----|----- |
|category |<b>true</b> |string |t(:dv_category)t(:dv_categorySuffix_1) |
|symbol |<b>true</b> |string |t(:row_comment_symbol) |

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|category |string |t(:dv_category)t(:dv_categorySuffix_1) |
|id |number |t(:row_comment_riskId)  |
|symbol|string |t(:row_comment_symbol) |
|limit |string |t(:risklimit) |
|maintainMargin |string |t(:row_comment_maintain_margin) |
|initialMargin |string |t(:dv_riskInitialMargin)  |
|section |string |t(:row_comment_section) |
|isLowestRisk |number |t(:row_comment_is_lowest_risk) |
|maxLeverage |string |t(:row_comment_max_leverage) |

### t(:dv_publictradingrecords)
> t(:codequote_curlExample)

```console
curl GET 'https://api-testnet.mufex.com/fapi/public/v1/market/trades?category=linear&symbol=BTCUSDT&limit=1'
```

```python--pybit

```


> t(:codequote_responseExample)

```javascript
{
    "code": 0,
    "message": "OK",
    "data":  {
        "category": "linear",
        "list": [
            {
                "execId": "0efadcdc-f1dd-5847-9185-2f0b40e81cc7",
                "symbol": "BTCUSDT",
                "price": "16871.00",
                "size": "0.006",
                "side": "Buy",
                "time": "1669802293550"
            }
        ]
    },
    "ext_info": {},
    "time": 1669802294719
}
```

t(:market_para_records)

<p class="fake_header">t(:httprequest)</p>
GET
<code><span id=dvrecentrades>/fapi/public/v1/market/trades</span></code>
<button class="clipboard_button" data-clipboard-action="copy" data-clipboard-target="#dvrecentrades"><img src="/images/copy_to_clipboard.png" height=15 width=15></img></button>

<p class="fake_header">t(:requestparameters)</p>
|t(:column_parameter)|t(:column_required)|t(:column_type)|t(:column_comments)|
|:----- |:-------|:-----|----- |
|category |<b>true</b> |string |t(:dv_category)t(:dv_categorySuffix_1) |
|symbol |<b>true</b> |string |t(:row_comment_symbol) |
|limit |false |int |t(:row_comment_limit_500_1000)|

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|category |string |t(:dv_category)t(:dv_categorySuffix_1) |
|execId |string |t(:dv_recentExecId)  |
|symbol |string |t(:row_comment_symbol) |
|price |number |t(:dv_recentPrice) |
|size |number |t(:row_response_comment_execqty) |
|t(:row_parameter_side) |string |t(:dv_recentSide) |
|time |string |t(:dv_recentTime) |


### t(:dv_marketopeninterest)
> t(:codequote_curlExample)

```console
curl GET 'https://api-testnet.mufex.com/fapi/public/v1/open-interest?category=linear&symbol=BTCUSDT&interval=1h&startTime=1657555200000&endTime=1657641600000'
```

```python--pybit

```

> t(:codequote_responseExample)

```javascript
{
    "code": 0,
    "message": "OK",
    "data":  {
        "symbol": "BTCUSDT",
        "category": "linear",
        "list": [
            {
                "openInterest": "15350.60700000",
                "timestamp": "1657641600000"
            },
            {
                "openInterest": "15605.74100000",
                "timestamp": "1657638000000"
            }
        ]
    },
    "ext_info": {},
    "time": 1669802294719
}
```

t(:market_para_marketopeninterest)

<p class="fake_header">t(:httprequest)</p>
GET
<code><span id=dvopeninterest>/fapi/public/v1/open-interest</span></code>
<button class="clipboard_button" data-clipboard-action="copy" data-clipboard-target="#dvopeninterest"><img src="/images/copy_to_clipboard.png" height=15 width=15></img></button>

<p class="fake_header">t(:requestparameters)</p>
|parameter|t(:column_required)|t(:column_type)|t(:column_comments)|
|:----- |:-------|:-----|----- |
|category |<b>true</b> |string |t(:dv_category)t(:dv_categorySuffix_1) |
|symbol |<b>true</b> |string |t(:row_comment_symbol) |
|interval |<b>true</b> |string |t(:dv_openInterInterval) |
|startTime |false |integer |t(:row_comment_startTime_ms) |
|endTime |false |integer |t(:row_comment_endTime_ms) |
|limit |false |integer |t(:row_comment_limit_50_200) |

<p class="fake_header">t(:responseparameters)</p>
|t(:column_parameter)|t(:column_type)|t(:column_comments)|
|:----- |:-----|----- |
|category |string |t(:dv_category)t(:dv_categorySuffix_1) |
|symbol |string |t(:row_comment_symbol) |
|openInterest |string |t(:row_comment_resp_open_interest) |
|timestamp |string |t(:dv_openInterTimestamp) |
