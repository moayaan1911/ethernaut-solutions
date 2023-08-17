Here is a full README file explaining the Fallout contract exploit:

# Exploiting the Fallout Contract

This contract is vulnerable due to a typo in the constructor name. Let's exploit it to steal the ETH!

## The Contract

The Fallout contract is deployed at:

https://mumbai.polygonscan.com/address/0xE178383D76c6EB68AaA78eBe3E330e2C22563a73

Here's what it does:

- Implements `allocate()` to allow funding allocations
- Allows withdrawals via `sendAllocation()` and `collectAllocations()`
- Has a buggy `Fal1out()` constructor that is never called 

This means the `owner` is never initialized!

## The Exploit

To exploit this contract:

1. Review the [source code](https://ethernaut.openzeppelin.com/level/0x0daf660d5b486796b008115a8e21c39febda8e91) and identify the `Fal1out` typo.

2. Deploy the vulnerable Fallout contract.

3. Write an interface contract with `Fal1out()` and `owner()`.

4. **Deploy the interface to the same address** as the vulnerable contract.

5. Call `Fal1out()` to run the constructor as the interface contract.

6. Call `owner()` to verify your address is now the owner.

7. Call `collectAllocations()` to drain all the ETH!

## Interface Contract

The interface contract code:

```solidity
interface Fallout {
  function Fal1out() external payable;
  function owner() external view returns (address);
} 
```

This mimics the original contract's methods to hijack ownership and steal the funds.

## Summary

The Fallout contract failed to initialize the owner due to a typo. By deploying an interface contract to the same address, we can simulate running the constructor to take ownership and drain the contract.

Let me know if you have any other questions!