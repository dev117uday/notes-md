# Contract

## Structure of Smart Contract

### Basics

**SPDX license**

**software package data exchange**

Trust in smart contract can be better established if their source code is available. Since making source code available always touches on legal problems with regards to copyright, the Solidity compiler encourages the use of machine-readable [SPDX license identifiers](https://spdx.org/). Every source file should start with a comment indicating its license:

Add the line `// SPDX-License-Identifier: MIT`

If you do not want to specify a or if the source code is not open-source, please use the special value `UNLICENSED`

#### Pragma

The `pragma` keyword is used to enable certain compiler features or checks. A pragma directive is always local to a source file, so you have to add the pragma to all your files if you want enable it in your whole project. If you [import](https://docs.soliditylang.org/en/v0.8.1/layout-of-source-files.html#import) another file, the pragma from that file does _not_ automatically apply to the importing file.

**Version Pragma**

Source files can \(and should\) be annotated with a version pragma to reject compilation with future compiler versions that might introduce incompatible changes. We try to keep these to an absolute minimum and introduce them in a way that changes in semantics also require changes in the syntax, but this is not always possible. Because of this, it is always a good idea to read through the changelog at least for releases that contain breaking changes. These releases always have versions of the form `0.x.0` or `x.0.0`.

#### ABI Coder Pragma

The standard ABI coder does not allow arrays of dynamic types, structs or nested variables between the Solidity contract and the dApp.

The ABI v2 coder; which allows structs, nested and dynamic variables to be passed into functions, returned from functions and emitted by events.

By using `pragma abicoder v1` or `pragma abicoder v2` you can select between the two implementations of the ABI encoder and decoder.

The new ABI coder \(v2\) is able to encode and decode arbitrarily nested arrays and structs. It might produce less optimal code and has not received as much testing as the old encoder, but is considered non-experimental as of Solidity 0.6.0. You still have to explicitly activate it using `pragma abicoder v2;`. Since it will be activated by default starting from Solidity 0.8.0, there is the option to select the old coder using `pragma abicoder v1;`

#### Importing other Source Files

Solidity supports import statements to help modularise your code that are similar to those available in JavaScript \(from ES6 on\). However, Solidity does not support the concept of a [default export](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export#Description).

At a global level, you can use import statements of the following form:

```js
import "filename";
import * as symbolName from "filename";
import "filename" as symbolName;
import {symbol1 as alias, symbol2} from "filename";
```

#### Comments

Single-line comments \(`//`\) and multi-line comments \(`/*...*/`\) are possible.

```js
// This is a single-line comment.

/*
This is a
multi-line comment.
*/
```

### Structure of a Contract

#### State Variables

State variables are variables whose values are permanently stored in contract storage.

```js
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.4.0 <0.9.0;

contract SimpleStorage {
    // State Variable
    uint storedData; 
}
```

* read more about types : [here](https://docs.soliditylang.org/en/v0.8.1/types.html#types)
* read more about getters and visibility : [here](https://docs.soliditylang.org/en/v0.8.1/contracts.html#visibility-and-getters)

#### Functions

Functions are the executable units of code. Functions are usually defined inside a contract, but they can also be defined outside of contracts.

```js
// SPDX-License-Identifier: GPL-3.0
pragma solidity >0.7.0 <0.9.0;

contract SimpleAuction {
    // Function
    function bid() public payable { 

    }
}

// Helper function defined outside of a contract
function helper(uint x) pure returns (uint) {
    return x * 2;
}
```

#### Function Modifiers

Function modifiers can be used to amend the semantics of functions in a declarative way Overloading, that is, having the same modifier name with different parameters, is not possible. Like functions, modifiers can be overridden.

```js
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.4.22 <0.9.0;

contract Purchase {
    address public seller;

    // Modifier
    modifier onlySeller() {
        require(
            msg.sender == seller,
            "Only seller can call this."
        );
        _;
    }

    function abort() public view onlySeller { // Modifier usage
        // ...
    }
}
```

## Understanding a Smart Contract

```js
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.8.0;

/**
 * @title Owner
 * @dev Set & change owner
 */
contract Owner {

    address private owner;

    // event for EVM logging
    event OwnerSet(address indexed oldOwner, address indexed newOwner);

    // modifier to check if caller is owner
    modifier isOwner() {
        // If the first argument of 'require' evaluates to 'false', execution terminates and all
        // changes to the state and to Ether balances are reverted.
        // This used to consume all gas in old EVM versions, but not anymore.
        // It is often a good idea to use 'require' to check if functions are called correctly.
        // As a second argument, you can also provide an explanation about what went wrong.
            require(msg.sender == owner, "Caller is not owner");
        _;
    }

    /**
     * @dev Set contract deployer as owner
     */
    constructor() {
        owner = msg.sender; // 'msg.sender' is sender of current call, contract deployer for a constructor
        emit OwnerSet(address(0), owner);
    }

    /**
     * @dev Change owner
     * @param newOwner address of new owner
     */
    function changeOwner(address newOwner) public isOwner {
        emit OwnerSet(owner, newOwner);
        owner = newOwner;
    }

    /**
     * @dev Return owner address 
     * @return address of owner
     */
    function getOwner() external view returns (address) {
        return owner;
    }
}
```

### Understanding a smart contract

* First line specifies the license : in this case GPL-3.0
* `pragma` is used to convey some message to compiler, like `once` in C++ to tell it to include this file onces. In this case, it is used to specify the range of versions of solidity compiler on which our code will work
* name of the contract : `Owner`
* contract variables
  * name : `owner`
  * type : `address`
  * visibility : `private`
* `event`
  * name of event : `OwnerSet`
  * event for EVM logging
* `modifier` :
  * name : `isOwner`
  * attached to : `changeOwner` function
  * will allow the `changeOwner` function to execute only when `msg.sender == owner`
  * else will print `Caller is not owner`
  * The function body is inserted where the special symbol "\_;" appears in the definition of a modifier. So if condition of modifier is satisfied while calling this function, the function is executed and otherwise, an exception is thrown.
* `constructor()` :
  * `msg.sender` is sender of current call, contract deployer for a constructor    
  * `emit OwnerSet(address(0), owner);` : emit the even `OwnerSet();`
* functions :
  * `changeOwner` :
    * arguments : `address newOwner`
    * visibility : `public`
    * modifier attached : `isOwner`
    * this event `OwnerSet` will trigger only after the modifier `isOwner` condition is satisfied
  * `getOwner`:
    * function is `external`, means anyone from outside the contract can call it
    * `view` is specified to tell the compiler that it will not modify any data
    * it `returns(address)`

