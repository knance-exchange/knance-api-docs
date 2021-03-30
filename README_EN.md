# API Developer's Guide

## Overview

Knance provides a simple and powerful REST API, allowing you to programmatically perform almost all operations in the web interface. All requests use the Application / JSON content type and https. The default URL is https://api.knance.com/version}/.

## Getting Started

General

certification

API reference

User library


## General

We provide a simple RESTful API. All calls are GET and must be called via https . The current stable API is v1. The standard format for endpoints is:


## API Reference

Our API is divided into 2 groups.

Public API: Public information that can be used without a key

Private API: A method of private transaction using a key

## Public API

https://api.knance.com/{version}/{method}

### /public/markets

Used to get the available trading markets at exchange.

Parameters

None

Request(GET):

https://api.knance.com/v1/public/markets

Response:
   
    {
        "result": true,
        "data": [
            {
                "coin": "BTC",
                "name": "Bitcoin",
                "fee": 0.005
            },
            {
                "coin": "ETH",
                "name": "Ethereum",
                "fee": 0.01
            },
            {
                "coin": "USDT",
                "name": "USD Tether",
                "fee": 1
            },
            {
                "coin": "XTC",
                "name": "XTrading24 Token",
                "fee": 1000
            },
            {
                "coin": "KRW",
                "name": "Korean Won",
                "fee": 1000
            }
        ]
    }

                        
### /public/summary/:market/:coin

Used to get summary for a given market

Parameters

parameter	required	description

market	required	a string literal for the market (ex: USDT)

coin	required	a string literal for the coin (ex: BTC)

Request(GET):

https://api.knance.com/v1/public/summary/USDT/BTC 

Response:
    
    {
        "result": true,
        "data": {
            "Market": "USDT",
            "High": 48406.6,
            "Low": 44336.3,
            "Last": 47451.4,
            "Volume": 18.716353239999986
        }
    }
                        

### /public/ticker/:market/:coin

Used to get retrieve the ticker for a given market

Parameters

parameter	required	description

market	required	a string literal for the market (ex: USDT)

coin	required	a string literal for the coin (ex: BTC)

Request(GET):

https://api.knance.com/v1/public/ticker/USDT/BTC 

Response:
    
    {
        "result": true,
        "data": {
            "time": "2021-02-27T01:06:50.919Z",
            "market": "USDT",
            "coin": "BTC",
            "price": 47451.6,
            "amount": 0.0072,
            "order": "buy"
        }
    }
    
                        

### /public/orderbook/:market/:coin

Used to get retrieve the orderbook for a given market

Parameters

parameter	required	description

market	required	a string literal for the market (ex: USDT)

coin	required	a string literal for the coin (ex: BTC)

Request(GET):

https://api.knance.com/v1/public/orderbook/USDT/BTC 

Response:

    {
        "result": true,
        "data": {
            "buy": [
                {
                    "price": 1400000,
                    "amount": 0.01
                },
                {
                    "price": 1300000,
                    "amount": 0.01
                },
                {
                    "price": 1200000,
                    "amount": 0.02
                }
            ],
            "sell": [
                {
                    "price": 2100000,
                    "amount": 0.02
                },
                {
                    "price": 2200000,
                    "amount": 0.01
                },
                {
                    "price": 2300000,
                    "amount": 0.01
                },
                {
                    "price": 2400000,
                    "amount": 0.01
                }
            ]
        }
    }`
                        `

### /public/trades/:market/:coin

Used to get retrieve the trades for a given market

Parameters

parameter	required	description

market	required	a string literal for the market (ex: USDT)

coin	required	a string literal for the coin (ex: BTC)

Request(GET):

https://api.knance.com/v1/public/trades/USDT/BTC 

Response:

    {
        "result": true,
        "data": [
            {
                "time": "2021-02-27T01:06:50.919Z",
                "market": "USDT",
                "coin": "BTC",
                "price": 47451.6,
                "amount": 0.0072,
                "side": "buy"
            },
            {
                "time": "2021-02-27T01:06:10.883Z",
                "market": "USDT",
                "coin": "BTC",
                "price": 47451.4,
                "amount": 0.0083,
                "side": "sell"
            },
            {
                "time": "2021-02-27T01:05:10.765Z",
                "market": "USDT",
                "coin": "BTC",
                "price": 47461.6,
                "amount": 0.0061,
                "side": "sell"
            },
            {
                "time": "2021-02-27T01:04:51.718Z",
                "market": "USDT",
                "coin": "BTC",
                "price": 47441.3,
                "amount": 0.0099,
                "side": "buy"
            }
        ]
    }
    
                        

### /public/charts/:market/:coin/:interval

Used to get retrieve the charts for a given market

Parameters

parameter	required	description

market	required	a string literal for the market (ex: USDT)

coin	required	a string literal for the coin (ex: BTC)

interval	required	a string literal for the interval (ex: 5)

Request(GET):

https://api.knance.com/v1/public/charts/USDT/BTC/5 

Response:

    {
        "result": true,
        "data": {
            "market": "USDT",
            "len": 6,
            "data": [
                {
                    "time": "2021-02-26T05:45:00.000Z",
                    "open": 46268.6,
                    "high": 46365.9,
                    "low": 46087.5,
                    "close": 46178.5,
                    "vol": 0.0422
                },
                {
                    "time": "2021-02-26T05:50:00.000Z",
                    "open": 46178.5,
                    "high": 46178.5,
                    "low": 45718.2,
                    "close": 45771.8,
                    "vol": 0.0664
                },
                {
                    "time": "2021-02-26T05:55:00.000Z",
                    "open": 45771.8,
                    "high": 45873,
                    "low": 45504.4,
                    "close": 45504.4,
                    "vol": 0.0693
                },
                {
                    "time": "2021-02-26T06:00:00.000Z",
                    "open": 45504.4,
                    "high": 45834.2,
                    "low": 45504.4,
                    "close": 45834.2,
                    "vol": 0.0351
                },
                {
                    "time": "2021-02-26T06:05:00.000Z",
                    "open": 45834.2,
                    "high": 46173.3,
                    "low": 45798.7,
                    "close": 46117.6,
                    "vol": 0.0745
                },
                {
                    "time": "2021-02-26T06:10:00.000Z",
                    "open": 46117.6,
                    "high": 46248.9,
                    "low": 46041.6,
                    "close": 46041.6,
                    "vol": 0.035199999999999995
                }
            ]
        }
    }              


## private API

certification

You can easily manage API key authentication. The system can have multiple API keys, each with a unique level of authority. To manage your API keys, go to Login -> API Settings.

Read information - You can only view your account balance, orders, and other details.

Transaction Limits - You can make LIMIT purchases and sales orders using API keys.

This version uses the standard HMAC-SHA512 signature. Add apikey and nonce to the request, calculate the HMAC hash and include it in the apisign header.


    // key.cfg 
    key="__YOUR_API_PUBLIC_KEY__";
    secret= "__YOUR_API_PRIVATE_KEY__";
                    
## Account Api

### /account/balance

Used to retrieve the balance from your account for a specific coin.

Parameters

parameter	required	description

coin	required	a string literal for the coin (ex: BTC)

Request(POST):

https://api.knance.com/v1/account/balance

Response:

    {
        "result": true,
        "data": {
            "asset": "BTC",
            "total": 9.9999999,
            "avail": 9.9499999,
            "hold": 0.05
        }
    }             
                            
    'use strict';

    const request = require('request');
    const env = require("node-env-file");
    env(__dirname + "/key.cfg");

    // Dev mode (insecure)
    process.env["NODE_TLS_REJECT_UNAUTHORIZED"] = 0;

    const nonce = new Date().getTime();
    const uri = 'https://api.knance.com/v1/account/balance'

    const signature = require("crypto")
        .createHmac("sha512", process.env.secret)
        .update(Buffer.from(uri, "utf-8"))
        .digest("hex");

    const data = {
        coin : 'BTC'
    }

    const options = {
        uri: uri,
        form: data,
        headers: {
        apikey: process.env.key,
        nonce: nonce,
        apisign: signature
        }
    };

    console.log(options);

    request.post(options, (err, resp, body) => {
        if (err) console.log(err);
        console.log(body);
    });
                                
                                                                                


### /account/order

Used to retrieve a single order by orderid.

Parameters

parameter	required	description

orderid	required	the orderid of the buy or sell order

Request(POST):

https://api.knance.com/v1/account/order

Response:

    {
        "result" : true,
        "data" : {
            "orderid" : "5fe7e3fa9aa6ea14c7ca9568"
            "market" : "USDT",
            "coin" : "BTC",
            "price" : 1200000,
            "amount" : 0.01
            "side" : "buy"
        }
    }
                            
    'use strict';
    const request = require('request');
    const env = require('node-env-file');
    env(__dirname + '/key.cfg');
    
    // Dev mode (insecure)
    process.env['NODE_TLS_REJECT_UNAUTHORIZED'] = 0
    
    const nonce = new Date().getTime();
    const uri = 'https://api.knance.com/v1/account/order'
    
    const signature = require("crypto")
        .createHmac("sha512", process.env.secret)
        .update(Buffer.from(uri, "utf-8"))
        .digest("hex");
    
    const data = {
        orderid : "5fe7e3fa9aa6ea14c7ca9568"
    }
    
    const options = {
        uri: uri,
        form: data,
        headers: {
        apikey: process.env.key,
        nonce: nonce,
        apisign: signature
        }
    };
    
    request.post(options, (err, resp, body) => {
        if (err) console.log(err);
        console.log(body);
    });
    
                                               


## Order Api

### /account/openorders

Get all orders that you currently have opened.

Parameters

parameter	required	description

market	required	 a string literal for the market (ex: USDT)

coin	required	a string literal for the coin (ex: BTC)


Request(POST):

https://api.knance.com/v1/account/openorders 

Response - Returns you the order orderid:

    {
        "result": true,
        "data": [
            {
            "id": "605af9ebfe8bb51aa9e11c7e",
            "time": "2021-03-24T08:35:55.868Z",
            "market": "USDT",
            "coin": "BTC",
            "price": 1200000,
            "amount": 0.01,
            "side": "buy"
            }
        ]
    }                                               
                        
    'use strict';

    const request = require('request');
    const env = require("node-env-file");
    env(__dirname + "/key.cfg");
    
    // Dev mode (insecure)
    process.env["NODE_TLS_REJECT_UNAUTHORIZED"] = 0;
    
    const currency = 'BTC';
    const nonce = new Date().getTime();
    const uri = 'https://api.knance.com/v1/account/openorders';
    
    const signature = require("crypto")
      .createHmac("sha512", process.env.secret)
      .update(Buffer.from(uri, "utf-8"))
      .digest("hex");
    
    const data = {
        market : 'USDT',
        coin : 'BTC'
    }
    
    const options = {
      uri: uri,
      form: data,
      headers: {
        apikey: process.env.key,
        nonce: nonce,
        apisign: signature
      }
    };
    
    console.log(options);
    
    request.post(options, (err, resp, body) => {
     if (err) console.log(err);
     console.log(body);
    });
    
                                            


### /order/buy

Used to place a buy order in a specific market. Use buy to place limit orders. Make sure you have the proper permissions set on your API keys for this call to work

Parameters

parameter	required	description

market	required	a string literal for the market (ex: USDT)

coin	required	a string literal for the coin (ex: BTC)

price	required	the price at which to place the order.

amount	required	the amount to purchase

Request(POST):

https://api.knance.com/v1/order/buy

Response - Returns you the order orderid:

    {
        "result": true,
        "data": {
            "orderid": "605afe73a869844006ad6b55"
        }
    }                      
                        
    'use strict';
    
    const request = require('request');
    const env = require('node-env-file');
    env(__dirname + '/key.cfg');
    
    // Dev mode (insecure)
    process.env['NODE_TLS_REJECT_UNAUTHORIZED'] = 0
    
    const uri = 'https://api.knance.com/v1/order/buy'
    const nonce = (new Date).getTime();
    const signature = require("crypto")
      .createHmac("sha512", process.env.secret)
      .update(Buffer.from(uri, "utf-8"))
      .digest("hex");
    
    const data = {
        market : 'USDT',
        coin  : 'BTC',
        price : 25000,
        amount : 0.1
    }
    
    const options = {
       uri: uri ,
       form: data,
       headers: {
           'apikey': process.env.key,
           'nonce': nonce,
           'apisign': signature
       }
    };
    
    request.post(options, (err, resp, body) => {
     if (err) console.log(err);
     console.log(body);
    });
        
                        


### /order/sell

Used to place an sell order in a specific market. Use selllimit to place limit orders. Make sure you have the proper permissions set on your API keys for this call to work

Parameters

parameter	required	description

market	required	a string literal for the market (ex: BTC-LTC)

price	required	the price at which to place the order.

amount	required	the amount to purchase

Request(POST):

https://api.knance.com/v1/order/sell

Response - Returns you the order orderid:

    {
        "result": true,
        "data": {
            "orderid": "605c1b04229dad66ec2f579e"
        }
    }                    
                        
    'use strict';
    
    const request = require('request');
    const env = require('node-env-file');
    env(__dirname + '/key.cfg');
    
    // Dev mode (insecure)
    process.env['NODE_TLS_REJECT_UNAUTHORIZED'] = 0
    
    const uri = 'https://api.knance.com/v1/order/sell'
    const nonce = (new Date).getTime();
    const signature = require("crypto")
      .createHmac("sha512", process.env.secret)
      .update(Buffer.from(uri, "utf-8"))
      .digest("hex");
    
    const data = {
        market : 'USDT',
        coin : 'BTC',
        price : 25000,
        amount : 0.1
    }
    
    const options = {
       uri: uri ,
       form: data,
       headers: {
           'apikey': process.env.key,
           'nonce': nonce,
           'apisign': signature
       }
    };
    
    request.post(options, (err, resp, body) => {
     if (err) console.log(err);
     console.log(body);
    });
    
    
                        


### /order/cancel

Used to cancel a buy or sell order.

Parameters

parameter	required	description

orderid	required	orderid of buy or sell order

Request(POST):
https://api.knance.com/v1/order/cancel

Response - Returns you the order id:

    {
        "result": true,
        "data": {
            "orderid": "605afc00a869844006ad6b51"
            }
        }
    }
                        
    'use strict';
    
    const request = require('request');
    const env = require('node-env-file');
    env(__dirname + '/key.cfg');
    
    // Dev mode (insecure)
    process.env['NODE_TLS_REJECT_UNAUTHORIZED'] = 0
    
    
    GetOrders(d => { 
      console.log("[DEBUG, GetOrders] " + JSON.stringify(d.data)); 
    
      if (d.data.length > 0) {
        var o = d.data[0];
        CancelOrder(o.id, data => { 
           console.log("[DEBUG, CanceOrder  uid " + JSON.stringify(data.result || data));
        });
      }
    
    });
    
    function CancelOrder(uuid, callback) {
        console.log("[DEBUG, CanceOrder  uuid " + uuid);
        const nonce = (new Date).getTime();
        const uri = 'https://api.knance.com/v1/order/cancel'
        const signature = require("crypto")
                          .createHmac("sha512", process.env.secret)
                          .update(Buffer.from(uri, "utf-8"))
                          .digest("hex");
        
        const data = {
           orderid : uuid
        }
        
        const options = {
            uri: uri,
            form: data,
            headers: {
                   'apikey': process.env.key,
                   'nonce': nonce,
                   'apisign': signature
            }
        }
        
        request.post(options, (err, resp, body) => {
         if (err) console.log(err);
          console.log(body)
        });
    };
    
    function GetOrders(callback) {
        const nonce = (new Date).getTime();
        const uri = 'https://api.knance.com/v1/account/openorders';
        const signature = require("crypto")
                          .createHmac("sha512", process.env.secret)
                          .update(Buffer.from(uri, "utf-8"))
                          .digest("hex");
        
        const data = {
          market : 'USDT',
          coin : 'BTC'
        }
    
        const options = {
            uri: uri,
            form: data,
            headers: {
                   'apikey': process.env.key,
                   'nonce': nonce,
                   'apisign': signature
            }
        }
    
        request.post(options, (err, resp, body) => {
         if (err) console.log(err);
           callback(JSON.parse(body))
        });
    };
                    
