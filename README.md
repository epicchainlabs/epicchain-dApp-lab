

<p align="center">
  EpicChain dApp Labpkit is the easiest way to build a dApp on Epicchain.
  <br/> Made by <b>xmoohad</b>
</p>

# EpicChain-dApp-labpkitt

EpicChain-dApp-labpkitt is the easiest way to build a dApp on EpicChain. Suitable to connect Web Applications, Off-chain JS Servers and 
React-Native Apps to the EpicChain Blockchain.

> [WalletConnectSDK](https://github.com/epicchainlabs/wallet-sdk) uses EpicChain-DappKit Types, so  you can easily swap
between EpicChain-DappKit implementation and WalletConnectSDK on the fly and reuse code, check the
[guide](/packages/epicchain-dApp-labpkit/WALLET-CONNECT.md).

## Installation
```sh
npm i @epicchainlabs/epicchain-dApp-labpkit
```

<details>
<summary>👉 For Vite Users</summary>

In the vite.config.ts file you must change the global value like this:
```ts
export default defineConfig({
    //your config here
	define: {
		global: 'globalThis',
        //...
	},
});
```
</details>

## Getting Started

EpicChain-Dappkit has 4 main components:
- [EpicChainInvoker](/packages/epicchain-dApp-labpkit/EpicChain-INVOKER.md): SmartContract Invocation Tool.
- [EpicChainParser](/packages/epicchain-dApp-labpkit/EpicChain-PARSER.md): Powerful Parser for EpicChain Types.
- [EpicChainSigner](/packages/epicchain-dApp-labpkit/EpicChain-SIGNER.md): Signs, Verifies, Encrypts and Decrypts data.
- [EpicChainEventListener](/packages/epicchain-dApp-labpkit/EpicChain-EVENT-LISTENER.md): Listen to events from the EpicChain Blockchain.


## Quick Example

```ts
import { NeonInvoker, NeonParser } from "@epicchainlabs/epicchain-dApp-labpkit";

const invoker = await NeonInvoker.init({
    rpcAddress: NeonInvoker.TESTNET,
})

const rawResp = await invoker.testInvoke({
    invocations: [
        {
            scriptHash: '0x123456',
            operation: 'myMethod',
            args: [123, 'Test'].map(NeonParser.formatRpcArgument)
        },
    ],
})

const resp = NeonParser.parseRpcResponse(rawResp.stack[0])
```

