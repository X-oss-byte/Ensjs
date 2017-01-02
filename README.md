<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

# ENS

Provides an easy-to-use interface to the Ethereum Name Service.

Example usage:

    var ENS = require('ethereum-ens');
    var Web3 = require('web3');

    var web3 = new Web3();
    var ens = new ENS(web3, '0x1234abc...');

    var address = ens.resolver('foo.eth').addr();

Throughout this module, the same optionally-asynchronous pattern as web3 is
used: all functions that call web3 take a callback as an optional last
argument; if supplied, the function returns nothing, but instead calls the
callback with (err, result) when the operation completes.

Functions that create transactions also take an optional 'options' argument;
this has the same parameters as web3.

**Parameters**

-   `web3` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** A web3 instance to use to communicate with the blockchain.
-   `address` **address** The address of the ENS registry.

**Meta**

-   **author**: Nick Johnson &lt;nick@ethereum.org>
-   **license**: LGPL

## resolver

resolver returns a resolver object for the specified name, throwing
ENS.NameNotFound if the name does not exist in ENS.
Resolver objects are wrappers around web3 contract objects, with the
first argument - always the node ID in an ENS resolver - automatically
supplied. So, to call the `addr(node)` function on a standard resolver,
you only have to call `addr()`.

**Parameters**

-   `name` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The name to look up.
-   `abi` **list** Optional. The JSON ABI definition to use for the resolver.
           if none is supplied, a default definition implementing `has`, `addr`
           and `setAddr` is supplied.
-   `callback` **[function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)** Optional. If specified, the function executes
           asynchronously.

Returns **any** The resolver object if callback is not supplied.

## setResolver

setResolver sets the address of the resolver contract for the specified name.
The calling account must be the owner of the name in order for this call to
succeed.

**Parameters**

-   `name` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The name to update
-   `address` **address** The address of the resolver
-   `options` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** An optional dict of parameters to pass to web3.
-   `callback` **[function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)** An optional callback; if specified, the
           function executes asynchronously.
-   `addr`  

Returns **any** The transaction ID if callback is not supplied.

## owner

owner returns the address of the owner of the specified name.

**Parameters**

-   `name` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The name to look up.
-   `callback` **[function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)** An optional callback; if specified, the
           function executes asynchronously.

Returns **any** The resolved address if callback is not supplied.

## setOwner

setOwner sets the owner of the specified name. Only the owner may call 
setResolver or setSubnodeOwner. The calling account must be the current
owner of the name in order for this call to succeed.

**Parameters**

-   `name` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The name to update
-   `address` **address** The address of the new owner
-   `options` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** An optional dict of parameters to pass to web3.
-   `callback` **[function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)** An optional callback; if specified, the
           function executes asynchronously.
-   `addr`  

Returns **any** The transaction ID if callback is not supplied.

## setSubnodeOwner

setSubnodeOwner sets the owner of the specified name. The calling account
must be the owner of the parent name in order for this call to succeed -
for example, to call setSubnodeOwner on 'foo.bar.eth', the caller must be
the owner of 'bar.eth'.

**Parameters**

-   `name` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The name to update
-   `address` **address** The address of the new owner
-   `options` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** An optional dict of parameters to pass to web3.
-   `callback` **[function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)** An optional callback; if specified, the
           function executes asynchronously.
-   `addr`  

Returns **any** The transaction ID if callback is not supplied.

# namehash

namehash implements ENS' name hash algorithm.

**Parameters**

-   `name` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** The name to hash

Returns **any** The computed namehash, as a hex string.