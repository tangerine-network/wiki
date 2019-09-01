Here's some sample code for creating and sending a verification transaction for your smart contract.

```javascript
// Node Version: 10.15.1
// NPM Version: 6.8.0
const Web3 = require('web3'); // Version: 1.0.0-beta.37
const EthereumTx = require('ethereumjs-tx'); // Version: 1.3.7


const web3 = new Web3('https://testnet-rpc.tangerine-network.io);
const myAddress = '0x89c24a88BaD4abE0A4F5b2EB5a86db1fb323832C';
const myPrivateKey = Buffer.from('61ce8b95ca5fd6f55cd97ac60817777bdf64f1670e903758ce53efc32c3dffeb', 'hex');
const message = 'Tangerine-DS';

web3
  .eth
  .getTransactionCount(myAddress)
  .then((count) => {
    const rawTx = {
      nonce: web3.utils.numberToHex(count),
      gasPrice: web3.utils.numberToHex(web3.utils.toWei('24', 'Gwei')),
      gasLimit: web3.utils.numberToHex('210000'),
      to: myAddress,
      value: web3.utils.numberToHex('0'),
      data: web3.utils.toHex(message),
    };
    const tx = new EthereumTx(rawTx);
    tx.sign(myPrivateKey);
    return tx.serialize();
  })
  .then((serializedTx) => {
    web3
      .eth
      .sendSignedTransaction(`0x${serializedTx.toString('hex')}`)
      .then((result) => {
        console.log(result);
      });
  });
```
