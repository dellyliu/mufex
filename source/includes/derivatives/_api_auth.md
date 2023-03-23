# t(:authentication)
<aside class="notice">
t(:auth_aside_key)
</aside>

<aside class="notice">
t(:auth_aside_env)
</aside>

t(:auth_para_privatepublic)

## t(:authenticationparameters)

## t(:constructingtherequest)
> t(:auth_codequote_construct1a_v3)


```http
GET /private/v1/trade/orders?category=option&symbol=BTC-29JUL22-25000-C HTTP/1.1
Host: api-testnet.mufex.com
-H 'MF-ACCESS-SIGN-TYPE: 2' \
-H 'MF-ACCESS-SIGN: eb431d99a1a203a434a82ac3ea8e107b5f94a967e9aaf922c41e84fb3ec9df78' \
-H 'MF-ACCESS-API-KEY: {api key}' \
-H 'MF-ACCESS-TIMESTAMP: 1658384431891' \
-H 'MF-ACCESS-RECV-WINDOW: 5000'
```

> t(:auth_codequote_construct3)

```http
POST /private/v1/trade/cancel HTTP/1.1
Host: api-testnet.mufex.com
-H 'MF-ACCESS-SIGN-TYPE: 2' \
-H 'MF-ACCESS-SIGN: c822337e76e30505e41b87a55af291e074f59f9496ba12ca2a57dc04fe65a178' \
-H 'MF-ACCESS-API-KEY: {api key}' \
-H 'MF-ACCESS-TIMESTAMP: 1658385589135' \
-H 'MF-ACCESS-RECV-WINDOW: 5000' \
-H 'Content-Type: application/json' \
-d '{
  "category": "option"
}'
```

t(:auth_para_construct3_dv3)

<aside class="notice">
t(:auth_aside_signature)
</aside>

<!--
### Examples of the Signature Algorithm

* [C#](https://github.com/bybit-exchange/bybit-official-api-docs/blob/master/en/example/Encryption.cs)
* [Python](https://github.com/bybit-exchange/bybit-official-api-docs/blob/master/en/example/Encryption.py)
* [C++](https://github.com/bybit-exchange/bybit-official-api-docs/blob/master/en/example/Encryption.cpp)
* [Go](https://github.com/bybit-exchange/bybit-official-api-docs/blob/master/en/example/Encryption.go)
* [PHP](https://github.com/bybit-exchange/bybit-official-api-docs/blob/master/en/example/Encryption.php)
-->


<script>
function copyStringToClipboard (endpoint) {
  var str = document.getElementById(endpoint).innerText;
  // remove whitespace
  var str = str.replace(/ /g,"");
  // Create new element
  var el = document.createElement("textarea");
  // Set value (string to be copied)
  el.value = str;
  // Set non-editable to avoid focus and move outside of view
  el.setAttribute("readonly", "");
  el.style = {position: "absolute", left: "-9999px"};
  document.body.appendChild(el);
  // Select text inside element
  el.select();
  // Copy text to clipboard
  document.execCommand("copy");
  // Remove temporary element
  document.body.removeChild(el);
}
</script>
