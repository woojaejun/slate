

# Account

## getbalances

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/account/getbalances";
const paramObject = {apikey: publicKey, nonce: now};
```

> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "Currency": "BTC",
    "Balance": 1061.499124105,
    "Available": 1059.270898105,
    "Pending": 2.228226,
    "CryptoAddress": "9Reb9uFHVhiAyHLF2XpWX1S3Y9UN5Gsc8N",
    "Requested": false,
    "Uuid": null
  }, {
    "Currency": "ETH",
    "Balance": 104845.910165684,
    "Available": 104840.905165684,
    "Pending": 5.005,
    "CryptoAddress": "MRWo92GtfAxVyJogQVf24mNKpdvmWfrGBJ",
    "Requested": false,
    "Uuid": null
  }]
}
```

This endpoint retrieves balances information.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/account/getbalances`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to get balances information

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to get balances information (optional)
apikey | The api key of the user to get balances information
walletid | The wallet id to get balances information (optional - default : the first trade wallet)


## getbalance

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/account/getbalance";
const paramObject = {apikey: publicKey, nonce: now, currency: 'btc'};
```

> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : {
    "Currency": "BTC",
    "Balance": 1061.499124105,
    "Available": 1059.270898105,
    "Pending": 2.228226,
    "CryptoAddress": "36FzdbtJB2WJyxFr1VKeTMtc4ncea9SfU4",
    "Requested": false,
    "Uuid": null
  }
}
```

This endpoint retrieves balance information of the wallet.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/account/getbalance`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to get balance information

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to get balance information (optional)
apikey | The api key of the user to get balance information
walletid | The wallet id to get balance information (optional - default : the first trade wallet)
currency | The currency to get balance information


## getdepositaddress

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/account/getdepositaddress";
const paramObject = {apikey: publicKey, nonce: now, currency: 'btc'};
```

> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : {
    "Currency": "BTC",
    "Address" : "3QR6Hr2pzRDCLgEqbFw4pJHJp5BVaDeYrL"
  }
}
```

This endpoint retrieves a deposit address.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/account/getdepositaddress`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to get a deposit address

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to get a deposit address (optional)
apikey | The api key of the user to get a deposit address
walletid | The wallet id to get a deposit address (optional - default : the first trade wallet)
currency | The currency to get a deposit address


## withdraw

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/account/withdraw";
const paramObject = {apikey: publicKey, nonce: now, currency: 'btc', 
      address: '32vuyKYN7wPzjPfWcjL7CZaq1XfV5TRmy5', quantity: '1', memo: 'hello'};
```


> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : {
    "uuid": "1234455"
  }
}
```

This endpoint withdraw the amount of the currency.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/account/withdraw`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to withdraw

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to withdraw (optional)
apikey | The api key of the user to withdraw
walletid | The wallet id to withdraw (optional - default : the first trade wallet)
currency | The currency to withdraw
address | The address of the wallet to withdraw
quantity | The amount of currencies to withdraw
memo | A simple memo to specify the purpose of this withdraw (optional - maximum of 50 characters)

<aside class="notice">
0.000000001 <= quantity <= 999999999.999999999<br>
# supported maximum decimal place number : 9 (ex : 0.000000001)
</aside>

## transferbetweenmywallets

```javascript
const method = "/account/transferbetweenmywallets";
const paramObject = {apikey: publicKey, nonce: now, currency: 'btc', 
      senderwalletid: '21', receiverwalletid: '1', quantity: '1', memo1: 'hello', memo2: 'ok'};
```

```json
{
  "success" : true,
  "message" : "",
  "result" : {
    "uuid": "1234455"
  }
}
```

This endpoint transfer currencies between your wallets.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/account/transferbetweenmywallets`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to transfer

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to transfer (optional)
apikey | The api key of the user to transfer
senderwalletid | The wallet id to send
receiverwalletid | The wallet id to receive
currency | The currency to transfer
quantity | The amount of currencies to transfer
memo1 | Memo to specify the purpose of this transfer (optional - maximum of 50 characters)
memo2 | Memo to leave on the receiving wallet (optional - maximum of 50 characters)

## gettransactionhistory

```javascript
const method = "/account/gettransactionhistory";
const paramObject = {apikey: publicKey, nonce: now, currency: 'btc', 
      walletid: '21', count: '1'};
```

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "id": "3435922142",
    "Type": "Credit",
    "Subtype": "Deposit",
    "WalletId": 21,
    "Currency": "DASH",
    "Amount": 0.002,
    "Fee": 0.00001,
    "Memo": "Hello",
    "AvailableBalance": 151535.15,
    "BalanceInUse": 0,
    "JobId": 159,
    "Time": "2018-12-25T09:10:35.12"
  },  {
    "id": "3435922142",
    "Type": "Credit",
    "Subtype": "Deposit",
    "WalletId": 21,
    "Currency": "DASH",
    "Amount": 0.002,
    "Fee": 0.00001,
    "Memo": "Hello",
    "AvailableBalance": 151535.15,
    "BalanceInUse": 0,
    "JobId": 159,
    "Time": "2018-12-25T09:10:35.12"
  }]
}
```

This endpoint retrieves transaction history data of the given wallet.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/account/gettransactionhistory`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to get transaction history data

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to get transaction history (optional)
apikey | The api key of the user to get transaction history
walletid | The wallet id to get transaction history (optional - ex : 21)
currency | The currency to get transaction history
count | The specific amount of the transaction history data (optional - default : 100, max : 1000)

## getorder

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/account/getorder";
const paramObject = {apikey: publicKey, nonce: now, uuid: '2457'};
```

> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : {
    "AccountId": null,
    "Uuid": null,
    "OrderUuid": "2457",
    "Exchange": "BTC-ETH",
    "OrderType": "LIMIT_SELL",
    "Quantity": 1,
    "QuantityRemaining": 0,
    "Limit": 1,
    "Reserved": 1,
    "ReserveRemaining": 0,
    "CommissionReserved": 0,
    "CommissionReserveRemaining": 0,
    "CommissionPaid": 1,
    "Price": 1,
    "PricePerUnit": 1,
    "Opened": "2018-12-20T2:25:46.19",
    "Closed": "2018-12-20T4:14:28.98",
    "IsOpen": false,
    "Sentinel": null,
    "CancelInitiated": false,
    "ImmediateOrCancel": false,
    "IsConditional": false,
    "Condition": null,
    "ConditionTarget": null
  }
}
```

This endpoint retrieves information of the order.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/account/getorder`


### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to get information of the order

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to get information of the order (optional)
apikey | The api key of the user to get information of the order
uuid | The uuid of the order to get information of the order


## getorderhistory

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/account/getorderhistory";
const paramObject = {apikey: publicKey, nonce: now, market: 'btc-eth'};
```

> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "OrderUuid": "17",
    "Exchange": "BTC-ETH",
    "TimeStamp": "2018-12-23T12:10:35.12",
    "OrderType": "LIMIT_BUY",
    "Limit": 0.00000002,
    "Quantity": 2,
    "QuantityRemaining": 2000,
    "Commission": 0,
    "Price": 2,
    "PricePerUnit": 2,
    "IsConditional": false,
    "Condition": null,
    "ConditionTarget": null,
    "ImmediateOrCancel": false
  }, {
    "OrderUuid": "2457",
    "Exchange": "BTC-ETH",
    "TimeStamp": "2018-12-20T4:14:28.98",
    "OrderType": "LIMIT_SELL",
    "Limit": 1,
    "Quantity": 1,
    "QuantityRemaining": 0,
    "Commission": 0.001,
    "Price": 1,
    "PricePerUnit": 1,
    "IsConditional": false,
    "Condition": null,
    "ConditionTarget": null,
    "ImmediateOrCancel": false
  }]
}
```

This endpoint retrieves an order history of markets.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/account/getorderhistory`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to get an order history

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to get an order history (optional)
apikey | The api key of the user to get an order history
market | The market to get an order history (optional - ex : eth-btc)
walletid | The wallet Id to get an order history (optional - ex : 21)
count | The specific amount of the order history data (optional - default : 300, max : 1000)

## getwithdrawalhistory

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/account/getwithdrawalhistory";
const paramObject = {apikey: publicKey, nonce: now, currency: 'btc'};
```
> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "PaymentUuid": "159",
    "Currency": "DASH",
    "Amount": 0.002,
    "Address": "9Hj3NDfdrhoNrBa9N1yr93WwrF4UwLhpFR",
    "Opened": "2018-11-26T1:25:17.82",
    "Authorized": true,
    "PendingPayment": false,
    "TxCost": 0,
    "TxId": "dea9c085e2574b41d804dd4e85c2d39206429ad6346bde05052775a538f32c0b",
    "Canceled": false,
    "InvalidAddress": false
  }, {
    "PaymentUuid": "3435921815",
    "Currency": "ETH",
    "Amount": 20,
    "Address": "0xf7723c7f5f4354bcdc7c3496749b4e51ff37d93f",
    "Opened": "2018-12-23T09:10:35.12",
    "Authorized": true,
    "PendingPayment": false,
    "TxCost": 0.2,
    "TxId": "0x938e96a86906de800c7d479eb7b33474b5975ac5b600f27b56d2a0254b84fa4c",
    "Canceled": false,
    "InvalidAddress": false
  }]
}
```

This endpoint retrieves a withdrawal history of the currency.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/account/getwithdrawalhistory`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to get a withdrawal history

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to get a withdrawal history (optional)
apikey | The api key of the user to get a withdrawal history
currency | The currency to get a withdrawal history (optional)
count | The specific amount of the withdrawal history data (optional - default : 100, max : 1000)

## getdeposithistory

```javascript
// please refer to skeleton codes in our authentication section.
const method = "/account/getdeposithistory";
const paramObject = {apikey: publicKey, nonce: now, currency: 'btc'};
```

> The above command returns JSON structured like this:

```json
{
  "success" : true,
  "message" : "",
  "result" : [{
    "PaymentUuid": "3435922142",
    "Currency": "DASH",
    "Amount": 0.002,
    "Address": "9Hj3NDfdrhoNrBa9N1yr93WwrF4UwLhpFR",
    "Opened": "2018-11-28T5:41:33.27",
    "Authorized": false,
    "PendingPayment": true,
    "TxCost": 0,
    "TxId": "dea9c085e2574b41d804dd4e85c2d39206429ad6346bde05052775a538f32c0b",
    "Canceled": false,
    "InvalidAddress": false
  },  {
    "PaymentUuid": "3883828",
    "Currency": "ETH",
    "Amount": 0.0012,
    "Address": "Xfc8DRahhdcbjunLWsdxmMUgdcg4C1nVrD",
    "Opened": "2018-12-25T09:10:35.12",
    "Authorized": true,
    "PendingPayment": false,
    "TxCost": 0.0000012,
    "TxId": "7dad1bb25a4756e9869d79ee32f0443e7d95571d9862266345915a5396fc1bca",
    "Canceled": false,
    "InvalidAddress": false
  }]
}
```

This endpoint retrieves a deposit history of the currency.

### HTTP Request

`GET https://api.dovewallet.com/v1.1/account/getdeposithistory`

### Header Settings

Key | Description
--------- | -----------
apisign | The api sign of the user to get a deposit history

### URL Parameters

Parameter | Description
--------- | -----------
nonce | The nonce to get a deposit history (optional)
apikey | The api key of the user to get a deposit history
currency | The currency to get a deposit history (optional)
count | The specific amount of the deposit history data (optional - default : 100, max : 1000)