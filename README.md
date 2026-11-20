# XRP to Dogecoin Price

An npm module that converts an amount of XRP into Dogecoin, for creating a market from XRP to Dogecoin on the Ripple network.

> **Status: dormant since 2014.** The last commit is from September 2014. It was a small 2014 experiment on the Ripple network. It depends on two services, the Cryptsy exchange API and the Ripple Charts API, and Cryptsy has since shut down, so it will not return a price today. This documentation pass did not run it.

Cryptsy and Ripple Charts are used to calculate the exchange rates.

## Install

    npm install --save xrp-to-dogecoin-price

Whether the package is still on the npm registry was not checked, so installing from a clone is safer:

    git clone https://github.com/stevenzeiler/xrp-to-dogecoin-price
    cd xrp-to-dogecoin-price
    npm install

## Usage

    var PriceFinder = require('xrp-to-dogecoin-price');
    var priceFinder = new PriceFinder();

    priceFinder.convert({
      xrp: 10000
    })
    .then(function(conversion) {
      console.log(conversion);
    })

The promise resolves to an object like `{ xrp: 10000, dog: <amount> }`.

## Configuration

None. There are no environment variables and no keys. The two endpoints are written into `index.js`.

## How it works

1. It asks Ripple Charts (`api.ripplecharts.com`) for the day's BTC/XRP exchange rate and turns the XRP amount into BTC.
2. It asks the Cryptsy public API (`pubapi.cryptsy.com`, market 132) for the last DOGE trade price and turns the BTC amount into DOGE.
3. It returns both numbers.

It uses `superagent` for HTTP and `bluebird` for promises.

## Files

- `index.js`: the `XrpToDogConverter` class (exported as the module).
- `bin/btc_to_dog`: a stub that only checks that a BTC amount was passed.
- `test/convert_xrp_to_dog.js`: one test that calls the live APIs and prints the result.

## Tests

    npm test

The script runs `mocha`, which is not listed in `package.json`, so install it first (`npm install --no-save mocha`). The only test calls the live APIs, so it cannot pass today. See `docs/STATUS.md`.

## License

ISC, as declared in `package.json`. See `LICENSE`.
