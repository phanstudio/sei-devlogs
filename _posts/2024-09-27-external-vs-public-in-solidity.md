---
layout: blog
title: "External Vs Public in Solidity"
date: 2024-09-27
---

# External Vs Public in Solidity
In Solidity, **`external`** is a function visibility keyword that determines how a function can be called and from where. Specifically, functions marked as `external` can only be called **from outside the contract**—by users, other contracts, or externally.

### Key Aspects of `external` in Solidity:

1. **Callable from Outside**:
   - `external` functions can be called by external actors (e.g., a user interacting with a contract or another smart contract).
   - You **cannot** call an `external` function internally from within the contract using the typical function call syntax (i.e., `this.functionName()` would be required to call it within the same contract).

2. **Gas Efficiency**:
   - Passing large amounts of data (such as arrays) to `external` functions is generally more gas-efficient than using `public` functions. This is because external functions receive data directly from **call data** (a part of the transaction that contains the function arguments).

3. **Internal Call Restriction**:
   - `external` functions can’t be called directly from within the contract. To call them from the same contract, you need to use `this.functionName()` (which is an external call and is less gas-efficient).

4. **Use Cases**:
   - Typically used when you expect the function to be called from outside the contract (e.g., user interactions or calls from other contracts).

### Example:

```solidity
pragma solidity ^0.8.0;

contract Example {
    // External function can be called from outside the contract
    function externalFunction(uint x) external returns (uint) {
        return x * 2;
    }

    // Public function can call external functions but uses 'this'
    function callExternalFunction(uint x) public view returns (uint) {
        // Calls the external function within the contract
        return this.externalFunction(x);
    }
}
```

### Key Differences Between `external` and Other Visibility Types:

1. **`external` vs. `public`**:
   - **External**: Can be called from outside the contract but not internally unless through `this`.
   - **Public**: Can be called both from inside and outside the contract.

2. **`external` vs. `internal`**:
   - **External**: Callable from outside the contract.
   - **Internal**: Only callable from within the contract or from contracts that inherit from it (but not from outside).

3. **`external` vs. `private`**:
   - **External**: Callable from outside the contract.
   - **Private**: Only callable within the contract where it’s defined, not even from derived contracts.

### Example with Internal Restriction:
If you try to call an `external` function directly from within the contract like a normal function, it will throw an error:

```solidity
pragma solidity ^0.8.0;

contract Example {
    function externalFunction(uint x) external returns (uint) {
        return x * 2;
    }

    function callExternalDirectly(uint x) public view returns (uint) {
        // This will cause an error, as external functions can't be called this way
        // return externalFunction(x);

        // Correct way to call external function within the contract
        return this.externalFunction(x);
    }
}
```

In summary, the **`external`** keyword defines functions that are intended to be called by entities outside the contract. It’s more efficient for passing large data and enforces that the function can't be called internally without explicitly using an external call method (`this.functionName()`).
