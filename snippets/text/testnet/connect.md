### HTTPS DNS

To connect to Thalesbase via HTTPS, simply point your provider to the following RPC DNS:

```
https://rpc.testnet.thales.network
```

For the web3.js library, you can create a local Web3 instance and set the provider to connect to Thalesbase (both HTTP and WS are supported):

```js
const Web3 = require('web3'); //Load Web3 library
.
.
.
//Create local Web3 instance - set Thalesbase as provider
const web3 = new Web3('https://rpc.testnet.thales.network'); 
```
For the ethers.js library, define the provider by using `ethers.providers.StaticJsonRpcProvider(providerURL, {object})` and setting the provider URL to Thalesbase:

```js
const ethers = require('ethers');


const providerURL = 'https://rpc.testnet.thales.network';
// Define Provider
const provider = new ethers.providers.StaticJsonRpcProvider(providerURL, {
    chainId: 1287,
    name: 'thalesbase-alphanet'
});
```

Any Ethereum wallet should be able to generate a valid address for Thales (for example, [MetaMask](https://metamask.io/)).

### WSS DNS

For WebSocket connections, you can use the following DNS:

```
wss://wss.testnet.thales.network
```

### Chain ID

For the Thalesbase TestNet the chain ID is: `1287`.
