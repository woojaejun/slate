

# Market

## buylimit

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/market/buylimit";
const paramObject = {apikey: publicKey, nonce: now, market: 'btc-eth', quantity: '3', rate: '1'};
```

> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : {
    "uuid": "5214"
  }
}
```

This endpoint places an order to buy.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/market/buylimit`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to place an order to buy

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to place an order to buy (optional)
apikey | The api key of the user to place an order to buy
market | The market pair of coins to trade with each other (ex : eth-btc)
quantity | The market to place an order to buy
rate | The market to place an order to buy
walletid | The wallet id to place an order to buy (optional - ex : 21)

<aside class="notice">
0.001 <= quantity <= 100000000<br>
0.000000001 <= rate <= 1000000000<br>
0.001 <= quantity * rate <= 100000000<br>
# supported maximum decimal place number : 9 (ex : 0.000000001)
</aside>

## selllimit

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/market/selllimit";
const paramObject = {apikey: publicKey, nonce: now, market: 'btc-eth', quantity: '3', rate: '1'};
```

> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : {
    "uuid": "1477"
  }
}
```

This endpoint places an order to sell.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/market/selllimit`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to place an order to sell

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to place an order to sell (optional)
apikey | The api key of the user to place an order to sell
market | The market to place an order to sell (ex : eth-btc)
quantity | The market to place an order to sell
rate | The market to place an order to sell
walletid | The wallet id to place an order to sell (optional - ex : 21)

<aside class="notice">
0.001 <= quantity <= 100000000<br>
0.000000001 <= rate <= 1000000000<br>
0.001 <= quantity * rate <= 100000000<br>
# supported maximum decimal place number : 9 (ex : 0.000000001)
</aside>

## cancel

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/market/cancel";
const paramObject = {apikey: publicKey, nonce: now, uuid: '157'};
```
> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : null
}
```

This endpoint places an order to cancel.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/market/cancel`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to place an order to cancel

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to place an order to cancel (optional)
apikey | The api key of the user to place an order to cancel
uuid | The uuid of the order to place an order to cancel
walletid | The wallet id to place an order to sell (optional - ex : 21)

## getopenorders

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/market/getopenorders";
const paramObject = {apikey: publicKey, nonce: now, market: 'btc-eth'};
```
> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "Uuid": null,
    "OrderUuid": "523",
    "Exchange": "BTC-ETH",
    "OrderType": "LIMIT_SELL",
    "Quantity": 15,
    "QuantityRemaining": 5,
    "Limit": 1,
    "CommissionPaid": 0,
    "Price": 0,
    "PricePerUnit": null,
    "Opened": "2018-12-23T12:10:35.12",
    "Closed": null,
    "CancelInitiated": false,
    "ImmediateOrCancel": false,
    "IsConditional": false,
    "Condition": null,
    "ConditionTarget": null
  }, {
    "Uuid": null,
    "OrderUuid": "578",
    "Exchange": "ETH-BTC",
    "OrderType": "LIMIT_BUY",
    "Quantity": 25,
    "QuantityRemaining": 5,
    "Limit": 1,
    "CommissionPaid": 0,
    "Price": 0,
    "PricePerUnit": null,
    "Opened": "2018-12-23T12:10:35.12",
    "Closed": null,
    "CancelInitiated": false,
    "ImmediateOrCancel": false,
    "IsConditional": false,
    "Condition": null,
    "ConditionTarget": null
  }]
}
```

This endpoint retrieves open orders information of the market.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/market/getopenorders`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to get open orders information

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to get open orders information (optional)
apikey | The api key of the user to get open orders information
market | The market to get open orders information (optional - ex : eth-btc)
walletid | The wallet id to get open orders infromation (optional - ex : 21)


