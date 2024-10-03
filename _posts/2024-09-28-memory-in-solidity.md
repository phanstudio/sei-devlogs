---
layout: blog
title: "Memory in solidity"
date: 2024-09-28
---

In Solidity, **`memory`** is one of the data location keywords used to specify where data should be stored during contract execution. Solidity uses different locations for storing data, such as **storage**, **memory**, and **stack**, each with different properties and use cases.

### Key Aspects of `memory` in Solidity:

1. **Temporary Storage**: 
   - Data stored in `memory` is temporary. It only exists during the execution of a function and is discarded when the function execution ends.
   - This makes `memory` suitable for storing temporary variables or data that you don’t need to persist between function calls.

2. **Non-Persistent**: 
   - Variables in `memory` are not written to the blockchain, so they don't persist after the function execution completes.
   - This makes it cheaper in terms of gas costs compared to storing data in **storage**, which is permanent and written to the blockchain.

3. **Explicit Declaration**:
   - When working with complex data types like arrays or structs in Solidity functions, you often need to explicitly specify that the data should be stored in `memory`.

4. **Use Case**:
   - Typically used for function parameters, return values, or any temporary computation.
   - Example: When passing an array or struct into a function, you would store it in `memory` if it’s only needed during that function’s execution.

### Example:

```solidity
pragma solidity ^0.8.0;

contract Example {
    // Storage variable (permanent)
    string public storedData;

    // Function that uses memory for a temporary variable
    function updateData(string memory newData) public {
        // `newData` exists only during this function call and is stored in memory
        storedData = newData;
    }

    // Function that returns a value stored in memory
    function getTempData() public pure returns (string memory) {
        string memory tempData = "This is temporary data";
        return tempData;
    }
}
```

### Breakdown:
- `newData`: The parameter is stored in `memory`, meaning it's only temporary and exists while the function is running.
- `tempData`: A string variable declared in `memory` that is returned by the function. It doesn’t persist beyond the function call.

### Why `memory` Matters:
- **Efficiency**: Since `memory` is cleared after a function execution, it’s more efficient for temporary operations.
- **Cost**: Data stored in `storage` is much more expensive in terms of gas because it requires writing to the blockchain. In contrast, `memory` is cheaper as it’s only used for the lifetime of a function.
- **Flexibility**: Functions often use `memory` when manipulating data without the need to permanently store it.
