# secp256k1-node

Version
-------
[![NPM Package](https://img.shields.io/npm/v/secp256k1.svg?style=flat-square)](https://www.npmjs.org/package/secp256k1)

[![js-standard-style](https://cdn.rawgit.com/feross/standard/master/badge.svg)](https://github.com/feross/standard)

[cryptocoinjs/secp256k1-node](https://github.com/cryptocoinjs/secp256k1-node#secp256k1-node)'s browser implementation (uses [elliptic](https://github.com/indutny/elliptic) will be used).

This library is experimental, so use at your own risk. Works on node version 4.0.0 or greater.

## Installation

##### from npm

`npm install secp256k1-pure`

##### from git

```
git clone git@github.com:davidmurdoch/secp256k1-pure.git
cd secp256k1-pure
npm install
```

## Usage

* [API Reference (v3.x)](https://github.com/cryptocoinjs/secp256k1-node/blob/master/API.md)

```js
const { randomBytes } = require('crypto')
const secp256k1 = require('secp256k1')
//   if you want to use pure js implementation in node

// generate message to sign
const msg = randomBytes(32)

// generate privKey
let privKey
do {
  privKey = randomBytes(32)
} while (!secp256k1.privateKeyVerify(privKey))

// get the public key in a compressed format
const pubKey = secp256k1.publicKeyCreate(privKey)

// sign the message
const sigObj = secp256k1.sign(msg, privKey)

// verify the signature
console.log(secp256k1.verify(msg, sigObj.signature, pubKey))
// => true
```

\* **.verify return false for high signatures**

## Second pure js implementation

Project has yet one secp256k1 implementation based on [elliptic](http://github.com/indutny/elliptic) and [bn.js](http://github.com/indutny/bn.js). The main purpose of this smaller size, high performance and easy code audit. This implementation is super experimental, use it at your own risk.

## LICENSE

This library is free and open-source software released under the MIT license.
