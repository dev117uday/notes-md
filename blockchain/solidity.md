# Solidity

## Solidity DataTypes

### Data types in Solidity

Solidity is a statically typed language, which means that the type of each variable (state and local) needs to be specified. Solidity provides several elementary types which can be combined to form complex types.

#### Booleans

`bool`: The possible values are constants true and false.

Operators:

* `!` (logical negation)
* `&&` (logical conjunction, “and”)
* `||` (logical disjunction, “or”)
* `==` (equality)
*   `!=`(inequality)

    The operators || and && apply the common short-circuiting rules. This means that in the expression `f(x) || g(y)`, if `f(x)` evaluates to true, `g(y)` will not be evaluated even if it may have side-effects.

#### Integers

`int` / `uint`: Signed and unsigned integers of various sizes. Keywords uint8 to `uint256` in steps of 8 (unsigned of `8` up to `256` bits) and int8 to int256. uint and int are aliases for `uint256` and `int256`, respectively.

**Operators:**

* Comparisons: `<=,`,`<`, `==`, `!=`, `>=`, `>` (evaluate to bool)
* Bit operators: `&`, `|`, `^` (bitwise exclusive or), `~` (bitwise negation)
* Shift operators: << (left shift), `>>` (right shift)
* Arithmetic operators: `+`, `-`, unary `-` (only for signed integers), `*`, `/`, `%` (modulo), `**` (exponentiation)
* For an integer type X, you can use `type(X).min` and `type(X).max` to access the minimum and maximum value representable by the type.

#### Address

The address type comes in two flavours, which are largely identical:

* address: Holds a 20 byte value (size of an Ethereum address).
* address payable: Same as address, but with the additional members transfer and send.
* The idea behind this distinction is that address payable is an address you can send Ether to, while a plain address cannot be sent Ether.

**Type conversions:**

Implicit conversions from address payable to address are allowed, whereas conversions from address to address payable must be explicit via `payable(<address>)`.

Explicit conversions to and from address are allowed for uint160, integer literals, bytes20 and contract types.

Only expressions of type address and contract-type can be converted to the type address payable via the explicit conversion payable(...). For contract-type, this conversion is only allowed if the contract can receive Ether, i.e., the contract either has a receive or a payable fallback function. Note that payable(0) is valid and is an exception to this rule.

#### Members of Addresses

**balance and transfer** It is possible to query the balance of an address using the property balance and to send Ether (in units of wei) to a payable address using the transfer function:

```js
address payable x = address(0x123);
address myAddress = address(this);
if (x.balance < 10 && myAddress.balance >= 10) x.transfer(10);
```

The transfer function fails if the balance of the current contract is not large enough or if the Ether transfer is rejected by the receiving account. The transfer function reverts on failure.

#### Enums

```js
enum ActionChoices { GoLeft, GoRight, GoStraight, SitStill }
```

#### Structs

```js
struct Campaign {
        address payable beneficiary;
        uint fundingGoal;
        uint numFunders;
        uint amount;
        mapping (uint => Funder) funders;
    }
```

#### Mapping Types

Mapping types use the syntax `mapping(_KeyType => _ValueType)` and variables of mapping type are declared using the syntax `mapping(_KeyType => _ValueType) _VariableName`. The `_KeyType` can be any built-in value type, `bytes`, `string`, or any contract or enum type. Other user-defined or complex types, such as mappings, structs or array types are not allowed. `_ValueType` can be any type, including mappings, arrays and structs.

```js
// SPDX-License-Identifier: GPL-3.0
pragma solidity >=0.4.0 <0.9.0;

contract MappingExample {
    mapping(address => uint) public balances;

    function update(uint newBalance) public {
        balances[msg.sender] = newBalance;
    }
}

contract MappingUser {
    function f() public returns (uint) {
        MappingExample m = new MappingExample();
        m.update(100);
        return m.balances(address(this));
    }
}
```

## Solidity Visibility

### Getters() and Visibility

Solidity knows two kinds of function calls: internal ones that do not create an actual EVM call (also called a “message call”) and external ones that do. Because of that, there are four types of visibility for functions and state variables.

Functions have to be specified as being `external`, `public`, `internal` or `private`. For state variables, `external` is not possible.

`external`

External functions are part of the contract interface, which means they can be called from other contracts and via transactions. An external function `f` cannot be called internally (i.e. `f()` does not work, but `this.f()` works). External functions are sometimes more efficient when they receive large arrays of data, because the data is not copied from calldata to memory. They can be called only from outside the contract

`public `Public functions are part of the contract interface and can be either called internally or via messages. For public state variables, an automatic getter function (see below) is generated.

`internal `**Those functions and state variables can only be accessed internally (i.e. from within the current contract or contracts deriving from it)**, without using `this`.

`private`**Private functions and state variables are only visible for the contract they are defined in and not in derived contracts.**

`pure`Solidity also contains pure functions, which means you're not even accessing any data in the app.

`view `: It's only viewing the data but not modifying it:
