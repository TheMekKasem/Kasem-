---
meta:
  - name: description
    content: Learn what the debug and trace APIs are and how to trace transactions on Polygon.
  - name: keywords
    content: polygon debug trace namespace transaction api geth bor
---

# Debug and trace APIs

A dedicated Polygon full or archive node has the `debug_*` API methods enabled. For the full list of the available debug and trace API methods, see [Debug namespace](https://geth.ethereum.org/docs/rpc/ns-debug).

## Usage examples

You can debug and trace transactions by replaying them in the Ethereum Virtual Machine to get the execution details in the exact same way as they happened on the chain.

Note that to debug and trace transactions, you need to have historical states on the node. Polygon full nodes keep historical states for the immediately previous 128 blocks. Polygon archive nodes keep historical states for the entire chain.

### debug_traceBlockByNumber

Trace all transactions included in a block with [debug_traceBlockByNumber](https://geth.ethereum.org/docs/rpc/ns-debug#debug_traceblockbynumber):

``` sh
curl -H "Content-Type: application/json" -d '{"id": 1, "method": "debug_traceBlockByNumber", "params": ["BLOCK_NUMBER"]}' ENDPOINT
```

where

* BLOCK_NUMBER — the number of the block to get the traces of included transactions.
* ENDPOINT — your node HTTPS endpoint.

See [View node access and credentials](/platform/view-node-access-and-credentials).

For example, trace all smart contract interactions in block 30848230:

``` sh
curl -H "Content-Type: application/json" -d '{"id": 1, "method": "debug_traceBlockByNumber", "params": ["30848230", {"tracer": "callTracer"}]}' https://nd-123-456-789.p2pify.com/3c6e0b8a9c15224a8228b9a98ca1531d
```

::: tip See also

* [EVM opcodes](https://ethereum.org/en/developers/docs/evm/opcodes)
* [Geth: debug namespace](https://geth.ethereum.org/docs/rpc/ns-debug)
* [Modes](/operations/polygon/modes)
* <a href="https://support.chainstack.com/hc/en-us/articles/900003400806-Tracing-EVM-transactions" target="_blank">Tracing EVM transactions</a>
* <a href="https://chainstack.com/evm-nodes-a-dive-into-the-full-vs-archive-mode/" target="_blank">EVM nodes: A dive into the full vs. archive mode </a>

:::