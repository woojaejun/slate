
# Public

## getmarkets

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/public/getmarkets";
const paramObject = {};
const options = {
    url: url
}
```

> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "MarketCurrency": "BTC",
    "BaseCurrency": "DASH",
    "MarketCurrencyLong": "Bitcoin",
    "BaseCurrencyLong": "Dash",
    "MinTradeSize": 0.001,
    "MarketName": "DASH-BTC",
    "IsActive": true,
    "Created": null
  }, {
    "MarketCurrency": "BTC",
    "BaseCurrency": "BAT",
    "MarketCurrencyLong": "Bitcoin",
    "BaseCurrencyLong": "Basic Attention Token",
    "MinTradeSize": 0.001,
    "MarketName": "BAT-BTC",
    "IsActive": true,
    "Created": null
  }]
}
```

This endpoint retrieves information of markets.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/public/getmarkets`


## getcurrencies

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/public/getcurrencies";
const paramObject = {};
const options = {
    url: url
}

```
> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "Currency": "BTC",
    "CurrencyLong": "Bitcoin",
    "MinConfirmation": 6,
    "TxFee": 0.001,
    "IsActive": true,
    "CoinType": null,
    "BaseAddress": null 
  }, {
    "Currency": "ESN",
    "CurrencyLong": "Ethersocial",
    "MinConfirmation": 30,
    "TxFee": 0,
    "IsActive": true,
    "CoinType": null,
    "BaseAddress": null
  }]
}
```

This endpoint retrieves information of currencies.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/public/getcurrencies`


## getticker

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/public/getticker";
const paramObject = {market: 'btc-eth'};
const options = {
    url: url + "?" + query
}
```
> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : {
    "Bid": null,
    "Ask": 0.2,
    "Last" : 0.2
  }
}
```

This endpoint retrieves ticker information of the market.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/public/getticker`

### URL Parameters

Parameter | Description
--------- | -----------
market | The market currency pair to get ticker information (ex : eth-btc)


## getmarketsummaries

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/public/getmarketsummaries";
const paramObject = {};
const options = {
    url: url
}
```
> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "MarketName": "BAT-ETH",
    "High": 0.0000052,
    "Low": 0.0000048,
    "Volume": 300.15877811,
    "Last": 0.0000051,
    "BaseVolume": 0.511223547,
    "TimeStamp" : "2018-12-20T2:30:51.47",
    "Bid" : 0.0000051,
    "Ask" : 0.00000512,
    "OpenBuyOrders" : 7,
    "OpenSellOrders" : 8,
    "PrevDay" : 0.000005,
    "Created" : "2018-11-21T8:52:00.00"
  }, {
    "MarketName": "BTC-ETH",
    "High": 0.0000054,
    "Low": 0.0000049,
    "Volume": 5778.12215788,
    "Last": 0.000005,
    "BaseVolume": 0.4,
    "TimeStamp" : "2018-12-20T2:30:51.47",
    "Bid" : 0.000005,
    "Ask" : 0.00000492,
    "OpenBuyOrders" : 20,
    "OpenSellOrders" : 55,
    "PrevDay" : 0.000004,
    "Created" : "2018-11-21T8:52:00.00"
  }]
}
```

This endpoint retrieves summaries of markets.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/public/getmarketsummaries`



## getmarketsummary

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/public/getmarketsummary";
const paramObject = {market: 'btc-eth'};
const options = {
    url: url + "?" + query
}
```

> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "MarketName": "BTC-ETH",
    "High": 0.0000054,
    "Low": 0.0000049,
    "Volume": 5778.12215788,
    "Last": 0.000005,
    "BaseVolume": 0.4,
    "TimeStamp" : "2018-12-20T2:30:51.47",
    "Bid" : 0.000005,
    "Ask" : 0.00000492,
    "OpenBuyOrders" : 20,
    "OpenSellOrders" : 55,
    "PrevDay" : 0.000004,
    "Created" : "2018-11-21T8:52:00.00"
  }]
}
```

This endpoint retrieves a summary of the market.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/public/getmarketsummary`

### URL Parameters

Parameter | Description
--------- | -----------
market | The market currency pair to get a summary (ex : eth-btc)


## getorderbook

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/public/getorderbook";
const paramObject = {market: 'btc-eth', type: 'both'};
const options = {
    url: url + "?" + query
}
```
> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : {
    "buy": [{
        "Quantity": 29, 
        "Rate": 0.5
    }],
    "sell" : [{
        "Quantity": 3, 
        "Rate": 2
      }, {
        "Quantity": 1.5, 
        "Rate": 1
    }]
  }
}
```

This endpoint retrieves an order book of the market.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/public/getorderbook`

### URL Parameters

Parameter | Description
--------- | -----------
market | The market currency pair to get an order book (ex : eth-btc)
type | The type of orders to get an order book (buy, sell, both)


## getmarkethistory

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/public/getmarkethistory";
const paramObject = {market: 'btc-eth'};
const options = {
    url: url + "?" + query
}
```
> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "Id": null,
    "TimeStamp": "2018-12-20T2:30:51.47",
    "Quantity": 60.18415689,
    "Price": 0.00001,
    "Total": 0.00060184,
    "FillType": null,
    "OrderType" : "BUY"
  }, {
    "Id": null,
    "TimeStamp": "2018-12-20T2:30:51.47",
    "Quantity": 21.18785511,
    "Price": 0.122,
    "Total": 2.58491832,
    "FillType": null,
    "OrderType" : "SELL"
  }]
}
```

This endpoint retrieves an order history of the market.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/public/getmarkethistory`

### URL Parameters

Parameter | Description
--------- | -----------
market | The market to get an order history (ex : eth-btc)


## gethistoricalmarkethistory

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/public/gethistoricalmarkethistory";
const paramObject = {market: 'btc-eth', limit: 10};
const options = {
    url: url + "?" + query
}
```
> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "Id": 1545273051471753,
    "TimeStamp": "2018-12-20T2:30:51.47",
    "Quantity": 60.18415689,
    "Price": 0.00001,
    "Total": 0.00060184,
    "FillType": null,
    "OrderType" : "BUY"
  }, {
    "Id": 1545273051471754,
    "TimeStamp": "2018-12-20T2:30:51.47",
    "Quantity": 21.18785511,
    "Price": 0.122,
    "Total": 2.58491832,
    "FillType": null,
    "OrderType" : "SELL"
  }]
}
```

This endpoint retrieves an historical order history of the market.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/public/gethistoricalmarkethistory`

### URL Parameters

Parameter | Description
--------- | -----------
market | The market to get an order history (ex : eth-btc)
limit  | The length of results (optional - default : 500)
fromid | The id of the order (optional - ex : 100122)