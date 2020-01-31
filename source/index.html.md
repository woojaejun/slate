---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript: node.js

toc_footers:
  - <a href='http://dovewallet.com' target='_blank'>Dove Wallet</a>
  - <a href='http://developer.dovewallet.com/api/v1.1' target='_blank'>API V1</a>

includes:
  - public
  - market
  - account
  - errors

search: true
---

# Introduction

Welcome to the Dovewallet API! You can use our API to access Dovewallet API endpoints, which can get information on various coin markets in our database.

We have language bindings in node.js! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

Our APIs basically follow the rules of bittrex APIs. 

<aside class="notice">
The `market` parameter follows the bittrex rules. A base currency is followed by a counter currency. Please make sure the order of markets.
<br>ex) btc-eth : btc - a base currency / eth - a counter currency
</aside>
<aside class="notice">
You can use the `market` parameter in an uppercase style.
</aside>

# Authentication

> To authorize, use this code:

```javascript
const crypto = require('crypto');
const request = require('request');
const querystring = require('querystring');

const BASE_URL = 'https://api.dovewallet.com/v1.1';
const method = "/market/buylimit";
const publicKey = "90d1415d13d8ea7061ccce5d26d99fe89c29b461";
const secretKey = "b9c100a09d553650dd8cbeaffc21d1";
const url = BASE_URL + method;
const now = Date.now();

const paramObject = {apikey: publicKey, nonce: now, market: 'dash-btc', quantity: '1', rate: '1'};
const query = querystring.stringify(objectSort(paramObject));
const apisign = crypto.createHmac('sha512', secretKey).update(url + "?" + query).digest('hex');

const options = {
    url: url + "?" + query,
    headers: {
        "apisign": apisign
    }
}

request(options, (error, response, body) => {
    if (error || response.statusCode != 200) {
        console.log(error, response.statusCode);
        return;
    }

    console.log(JSON.stringify(body));
});

function objectSort(object) {
    let newObject = Object.create(null);
    for(let key of Object.keys(object).sort()) {
        newObject[key] = object[key];
    }
    return newObject;
}
```

> Make sure to replace `publicKey, secretKey` with your API keys. and please replace `method, parameters` with what you want.

Dovewallet uses API keys to allow access to the private APIs. You can register a new Dovewallet API key on our [my-page/api](https://dovewallet.com/my-page/api) page.

Dovewallet expects for the apisign to be included in private API requests to the server in a header that looks like the following:

`apisign: 0ba5264acef900423cb31f02a6f1a2933e64004fbeb2f0187135665a73e5afabdd4eef3d41dcf8b9ef929793b332b1e2e75401190411cfb4372bc3eabb6bb40b`

<aside class="notice">
You must make an apisign with your personal API keys.
</aside>