# Kayros Wallet Developer Guide

## Detect Kayros Wallet

The presence of the kayrosWallet boolean variable, `window.kayrosWallet`, in a user's browser indicates a Kayros Wallet user.
To demonstrate this, verify if your browser is running Kayros Wallet by copying and pasting the following code snippet in the developer console of your browser:

```javascript
if (typeof window.kayrosWallet === 'boolean' && window.kayrosWallet === true) {
  console.log('Kayros Wallet is installed!');
}
```

if the `kayrosWallet` variable is set to true it means that you can use the Ethereum provider object, `window.ethereum`, with your favorite library. In the examples below we use the `ethers` library.

## Using Kayros Wallet with `ethers`

1. Download and install the `ethers` library https://ethers.org/.

2. Use `windows.ethereum` to get an instance of a web3 provider:
```javascript
const provider = new ethers.providers.Web3Provider(window.ethereum);
```

3. Check the connected network with:
```javascript
const network = await provider.getNetwork();
if (network.chainId !== 137) {
  console.error("Please connect to Polygon");
}
```

4. Sign a transaction with:
```javascript
const signer = provider.getSigner();
// Send 1 ether to an ens name.
const tx = signer.sendTransaction({
    to: "patrick.kayros.eth",
    value: ethers.utils.parseEther("1.0")
});
```

For more examples please refer to the documentation of your favorite library (`ethers`, `web3js`, ...).


