
# Fallback Contract

- Deployed on Mumbai Polygon testnet: https://mumbai.polygonscan.com/address/0x62A897C33737f25CFd3d2834A3523e779CB12341

## About the Contract

- Keeps track of `contributions` mapping from addresses to amounts
- Constructor sets `owner` to deployer address and gives them initial contribution
- `contribute()` allows sending ETH up to 0.001 ETH, which is added to sender's contributions
- If new contribution makes contributor the largest, they become the new `owner`
- `getContribution()` returns the contribution amount for a user 
- `withdraw()` allows the `owner` to withdraw all ETH in the contract
- `receive()` fallback function allows receiving ETH 
- If ETH is received, the sender becomes the new `owner` if they already have contributions
- To solve:
  - Need to call `contribute()` to have non-zero contributions
  - Then trigger the `receive()` fallback by sending ETH to withdraw funds

